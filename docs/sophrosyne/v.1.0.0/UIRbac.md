# RBAC Model
Sophrosyne supports 3 types/roles of Users: 
* <b>admin</b>
* <b>user</b>
* <b>client</b>

Each user role has different types of access and rights in Sophrosyne. The associated restrictions are not only a frontend implementation but also enforced on the server side for maximum security.

## Admin
Admin(s) have the maximum access and rights. They can access any Sophrosyne related functionality as well as the Apikey-Management, User-Management and export the complete Sophrosyne-Instance. These extra functionalities, can be found under the Admin Area.

<div style="text-align: center">
<img src="/sophrosyne/v.1.0.0/_media/RBAC_ADMIN_VIEW.png" alt="RBAC_ADMIN_VIEW" style="max-height:50vh">
</div>

## User
User(s) can access any Sophrosyne related functionality. However in contrast to Admin(s), they cannot access the Apikey-Management, User-Management and export the complete Sophrosyne-Instance. Hence, they can not access the Admin Area.

<div style="text-align: center">
<img src="/sophrosyne/v.1.0.0/_media/RBAC_USER_VIEW.png" alt="RBAC_USER_VIEW" style="max-height:50vh">
</div>

## Client
Client(s) have only restricted access to Sophrosyne related functionality. They can only access and trigger Actions, that are assigned to them by admins and/or users. They can confirm any Actions, even if those are <b>not</b> assigned to them. Additionally, they can receive Action Recommendations. Furthermore, they can only view information

<div style="text-align: center">
<img src="/sophrosyne/v.1.0.0/_media/RBAC_CLIENT_VIEW.png" alt="RBAC_CLIENT_VIEW" style="max-height:50vh">
</div>
