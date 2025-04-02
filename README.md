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
