
########
accounts
########


****
NAME
****


ncm-accounts: NCM component to manage the local accounts on the machine.


***********
DESCRIPTION
***********


The \ *accounts*\  component manages the local accounts on a machine. LDAP
authentication depends on the LDAP configuration, which is handled by
\ ``ncm-authconfig``\ .

Shadowing of passwords is also controlled by \ ``ncm-authconfig``\ .


*********
FUNCTIONS
*********


accounts provides several functions as an API to handle creation of users and groups.
They are mainly targeted at helping creating consistent accounts across machines,
using a central definition of all accounts and a per machine list of accounts to be
actually created.

All these functions update a structure_accounts (return value may be assigned to
"/software/components/accounts").

Behaviour of these functions can be customized by definining some variables before
calling them, mainly :


ACCOUNTS_USER_HOME_ROOT
 
 defines default root for home directory (Default: \ ``/home``\ )
 


ACCOUNTS_USER_CREATE_HOME
 
 defines if home directory must be created by default (Default: \ ``true``\ )
 


ACCOUNTS_USER_AUTOGROUP
 
 defines if a group must be defined with the same name as the user, if no group
 has been explicitly specified (Default: \ ``true``\ ).
 


ACCOUNTS_USER_CHECK_GROUP
 
 defines if the default group must be created if it doesn't exist, with a gid
 equals to uid (Default: \ ``true``\ )
 


ACCOUNTS_USER_COMMENT
 
 defines a default value for user comment (Default: \ ``Created by ncm-accounts``\ )
 


ACCOUNTS_GROUP_COMMENT
 
 defines a default value for group comment (Default: \ ``Created by ncm-accounts``\ )
 


create_accounts_from_db(userList:nlist, users:list:optional, accountType:optional)
==================================================================================


This function creates users or groups from a nlist containing user or group characteristics.
It updates a structure_accounts (return value may be assigned to \ ``/software/components/accounts``\ ).

User/group characteristics must be provided as structure_userinfo/structure_groupinfo.

Second parameter, if presents, gives the list of users to create from user_list.
This allows to use a unique user/group definition for all nodes, to warrant consistency
between nodes.

By default (accountType undefined or 0), this function creates user accounts.
To create groups, set third parameter (accountType) to 1.


create_group(groupname:string, params:structure_groupinfo)
==========================================================


This function creates a group, applying some defaults defined by variables and checking
information consistency.
It updates a structure_accounts (return value may be assigned to \ ``/software/components/accounts``\ ).


create_user(username:string, params:structure_userinfo)
=======================================================


This function creates a user, applying some defaults defined by variables and checking
 information consistency (e.g. group existence).
It updates a structure_accounts (return value may be assigned to Default: \ ``/software/components/accounts``\ ).


keep_user_group(user_or_group:string or list of string)
=======================================================


This functions adds a user or group to the kept_users or kept_groups resources. The
argument can be a string or list of strings. The return value can be assigned to 
\ ``/software/components/accounts/kept_users``\  or \ ``/software/components/accounts/kept_groups``\ .



*********
RESOURCES
*********


\ ``/software/components/accounts/rootpwd``\ 
=============================================


The crypted root password for the machine.


\ ``/software/components/accounts/users``\ 
===========================================


An nlist of users to configure on the node.  The key is the account
name (or base name for pool accounts). The numerical UID is
mandatory. The available fields are:


comment
 
 real name or comment about user.  Defaults to user name itself.
 


homeDir
 
 full path of the home directory of the user.  Defaults
 to the system default. For pool accounts this will be used as a
 base for creating numbered home directories; if this is not set
 the username will be used as a base.
 


createHome
 
 boolean indicating whether to create a home directory for the user.
 Defaults to false.
 


groups
 
 a list of groups for this user.  The first group listed
 is the primary group.  If this is not given, then it will default to a
 group named identically to the user name. NOTE: If this group already
 exists, then the command to add the user will fail.
 


password
 
 the crypted password entry for the user.  No
 default. If not given it will result in a locked account, except if
 the account already exists and has a defined password: in this case, it will
 be kept.
 


shell
 
 the shell for the user. If it is defined as an empty string, the current shell
 is preserved for an existing account (for a new account, it will remain undefined,
 meaning that the default shell on the system will be used).
 
 Defaults to /bin/bash.
 


uid
 
 the uid value for this account. Mandatory. This is interpreted as the
 base uid value for pool accounts (i.e. poolSize > 0).
 


poolStart
 
 the index at which to start the pool accounts.  The
 default is 0.  This must be a non-negative number.
 


poolDigits
 
 the number of digits to which the pool account
 numbers are padded. For example a value of 3 will create accounts
 atlas000, atlas001, etc. The default is the number of digits in the
 highest-numbered pool account.
 


poolSize
 
 number of pool accounts to create.  The default is
 0 which indicates that it is a normal (unique) account.  A value
 greater than 0 will create a set of numbered accounts with the given
 user name as a base.  E.g. a base name of "atlas" and a poolSize=3
 will create three accounts atlas0 atlas1 atlas2.
 



\ ``/software/components/accounts/groups``\ 
============================================


An nlist of groups to configure on the node.  The key is the group
name.  At least one field must be specified.


comment
 
 ignored, but provided so gid doesn't have to be
 


gid
 
 the optional gid number for the group
 


requiredMembers
 
 An optional list of users that must be added as member of the group. The users don't have to be
 local users, defined in the configuration.
 
 Note 1: group members present in the \ */etc/group*\  file but not defined in the current configuration 
 are removed by \ **ncm-accounts**\  if they are not required members.
 
 Note 2: for users defined in the configuration the preferred way to add them to groups is by defining
 their \ ``groups``\  property.
 


replaceMembers (boolean)
 
 When true, current members of the group (if existing) are replaced by the groups defined in the
 configuration (coming from \ ``requiredMembers``\  and user groups). If false, groups from the
 configuration are merged with existing ones.
 
 D: false
 



\ ``/software/components/accounts/login_defs``\ 
================================================


A nlist of values to be set in /etc/login.defs. NOTE: This
configuration file is specific to RedHat-like systems; setting will be
ignored on other systems.  This file configures all kinds of default
settings such as:


uid_min, uid_max
 
 Min/max values for automatic uid selection in useradd.
 


gid_min, gid_max
 
 Min/max values for automatic gid selection in groupadd.
 


pass_max_days
 
 Maximum number of days a password may be used.
 


pass_min_days
 
 Minimum number of days allowed between password changes.
 


pass_min_len
 
 Minimum acceptable password length.
 


pass_warn_age
 
 Number of days warning given before a password expires.
 


create_home
 
 If useradd should create home directories for users by default.
 



\ ``/software/components/accounts/remove_unknown``\ 
====================================================


Flag to indicate whether unknown accounts should be deleted.  The
default is false.  The root account can never be removed.


\ ``/software/components/accounts/preserved_accounts``\ 
========================================================


This property may have 3 values: 'none', 'system', 'dyn_user_group'. It controls
the accounts/groups that have to be preserved when \ ``remove_unknown``\  is true 
(it has no effect when \ ``remove_unknown=false``\ ).

The effect of each possible value is:


system
 
 all accounts/groups in the system range (strictly below GID/UID_MIN as
 defined in /etc/login.defs) are preserved even though they are not present
 in the configuration. It is possible to use login_defs/uid_min and
 login_defs/gid_min properties to control the preserved ranges.
 


dyn_user_group
 
 all accounts/groups in the system range and in the
 range used for dynamic uid/gid allocation by useradd command, ie. all
 accounts/groups with uid/gid less or equal to GID/UID_MAX as defined in 
 /etc/login.defs, are preserved. The exact list of accounts preserved
 depends on UID/GID_MAX value. It is possible to use login_defs/uid_max and
 login_defs/gid_max properties to control the preserved ranges. Not that
 \ ``remove_unknown=true``\  with preserved_accounts=dyn_user_group and UID/GID_MAX
 set to the highest possible IDs is equivalent to \ ``remove_unknown=false``\ .
 


none
 
 all existing accounts/groups not present in the configuration are
 removed from the system (except root).
 


\ ** Default: **\  \ ``dyn_user_group``\ 



***********
LIMITATIONS
***********


Local users belonging to LDAP groups
====================================


When a local user has to belong to a group defined only on LDAP, a
local group with the desired numerical ID is created.

This group has the same name as the user ID. It will be removed on the
next run of the component if \ ``remove_unknown``\  is set to true. This is
somewhat ugly, but doesn't affect the system behaviour at all, so it
\ **won't**\  be fixed.


nsswitch.conf status
====================


The component has been tested with \ ``files``\  as the primary source on
\ ``/etc/nsswitch.conf``\  for \ ``group``\  and \ ``passwd``\ . Different settings may
produce strange behaviour. These settings are not controlled by
ncm-accounts but by \ ``ncm-authconfig``\ .


