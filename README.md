# ThetaEdgeCloud Platform Services API Specifications

This document provides specifications for the ThetaEdgeCloud (TEC) API used to manage projects and users in a ThetaEdgeCloud organization.

## Base URL

```
https://api.thetaedgecloud.com
```

## Authentication

All API requests require authentication using an API key. The API key should be included in the request headers as `x-api-key`.

```
x-api-key: your_tec_api_key_here
```

## API Endpoints

### Retrieve Project

Retrieve a project in your ThetaEdgeCloud organization.

- **URL**: `/project/{tec_project_id}`
- **Method**: `GET`
- **Headers**:
  - `x-api-key`: Your ThetaEdgeCloud API key

**Example Request**:
```curl
curl -H 'x-api-key: {TEC_API_KEY}' https://api-beta.thetaedgecloud.com/project/{tec_project_id}
```

**Response**:

```json
{
   "status":"success",
   "body":{
      "projects":[
         {
            "id":"prj_9uxm3drw0ka0t96g8k3pdb6p697a",
            "name":"Project X",
            "org_id":"org_5b0sj4id6m7kdsz3qgs4q2nh1vz4",
            "tva_id":"srvacc_xqznwzp652eumcz476mhh8pzm",
            "gateway_id":null,
            "create_time":"2024-03-20T21:34:58.754Z"
         }
      ]
   }
}
```

### Update Project

Update a project in your ThetaEdgeCloud organization.

- **URL**: `/project/{tec_project_id}`
- **Method**: `PUT`
- **Headers**:
  - `x-api-key`: Your ThetaEdgeCloud API key
  - `Content-Type`: `application/json`
- **Request Body**:
  - `name`: The new name of the project
 
**Example Request**:
```curl
curl -X PUT -H "Content-Type: application/json" -H 'x-api-key: {TEC_API_KEY}' https://api-beta.thetaedgecloud.com/project/{tec_project_id}
-d '{"name": "Project Z"}'
```

**Response**:

```json
{
   "status":"success",
   "body":{
      "projects":[
         {
            "id":"prj_9uxm3drw0ka0t96g8k3pdb6p697a",
            "name":"Project Z",
            "org_id":"org_5b0sj4id6m7kdsz3qgs4q2nh1vz4",
            "tva_id":"srvacc_xqznwzp652eumcz476mhh8pzm",
            "gateway_id":null,
            "create_time":"2024-03-20T21:34:58.754Z"
         }
      ]
   }
}
```

### Retrieve Project Users

Retrieve all project member users

- **URL**: `/project/{tec_project_id}/users`
- **Method**: `GET`
- **Headers**:
  - `x-api-key`: Your ThetaEdgeCloud API key

**Example Request**:
```curl
curl -H 'x-api-key: {TEC_API_KEY}' https://api-beta.thetaedgecloud.com/project/{tec_project_id}/users
```

**Response**:

```json
{
   "status":"success",
   "body":{
      "users":[
         {
            "id":"usr_5kyver75cswdi2s2u4eby1d7dxyx",
            "first_name":"John",
            "last_name":"Doe",
            "avatar_url":null,
            "create_time":"2024-03-20T21:34:58.754Z",
            "email":"john@sliver.tv",
            "role":"admin",
            "disabled":false
         },
         {
            "id":"usr_eupuhevnvdai19urm7j6dt5ee49p",
            "first_name":"Emma",
            "last_name":"Watson",
            "avatar_url":null,
            "create_time":"2025-03-06T22:42:34.318Z",
            "email":"emma@thetalabs.org",
            "role":"viewer",
            "disabled":false
         }
      ]
   }
}
```

### Add User to Project

Add a user to project.

- **URL**: `/project/{tec_project_id}/user`
- **Method**: `POST`
- **Headers**:
  - `x-api-key`: Your ThetaEdgeCloud API key
  - `Content-Type`: `application/json`
- **Request Body**:
  - `user_id`: The new user's id
  - `role`: The role of the new user in the project. Value could be: `admin`, `editor` or `viewer`
 
**Example Request**:
```curl
curl -X POST -H "Content-Type: application/json" -H 'x-api-key: {TEC_API_KEY}' https://api-beta.thetaedgecloud.com/project/{tec_project_id}/user
-d '{"user_id": "usr_a61vds5nc7th6jcz6x0xra34y9e4", "role": "viewer"}'
```

**Response**:

```json
{
   "status":"success",
   "body":{
      "model":"users",
      "models":{
      },
      "id":"usr_a61vds5nc7th6jcz6x0xra34y9e4",
      "role":"viewer",
      "create_time":"2025-04-01T23:08:12.764Z",
      "disabled":false
   }
}
```

### Disable User in Project

Disable a project member.

- **URL**: `/project/{tec_project_id}/user/{tec_user_id}`
- **Method**: `DELETE`
- **Headers**:
  - `x-api-key`: Your ThetaEdgeCloud API key
 
**Example Request**:
```curl
curl -X DELETE -H 'x-api-key: {TEC_API_KEY}' https://api-beta.thetaedgecloud.com/project/{tec_project_id}/user/{tec_user_id}
```

**Response**:
A 204 status code

### (Re)Eable User in Project

Re-enable a previously disabled project member.

- **URL**: `/project/{tec_project_id}/user/{tec_user_id}/enable`
- **Method**: `PUT`
- **Headers**:
  - `x-api-key`: Your ThetaEdgeCloud API key
 
**Example Request**:
```curl
curl -X PUT -H 'x-api-key: {TEC_API_KEY}' https://api-beta.thetaedgecloud.com/project/{tec_project_id}/user/{tec_user_id}/enable
```

**Response**:
```json
{
   "status":"success",
   "body":{
      "model":"users",
      "models":{
      },
      "id":"usr_a61vds5nc7th6jcz6x0xra34y9e4",
      "role":"viewer",
      "create_time":"2025-04-01T23:08:12.764Z",
      "disabled":false
   }
}
```
