# ...generate REST API with Swagger and Bootprint

## Modules 

```bash
npm install -g bootprint bootprint-swagger
```

## Command line

```bash
bootprint swagger ./src/docs/restapi.json ./build/docs/v1
```

## Files

#### docs/restapi.json

```json
{
    "swagger": "2.0",
    "info": {
        "title": "Project Name",
        "description": "Project description",
        "version": "0.1.0"
    },
    "host": "api.project.com",
    "schemes": [
        "http",
        "https"
    ],
    "basePath": "/",
    "produces": [
        "application/json"
    ],
    "paths": {
        "/crud": {
            "get": {
                "summary": "Short description",
                "description": "A very lorem ipsum dolor sit amet long description\n",
                "responses": {
                    "200": {
                        "description": "Returns something",
                        "schema": {
                            "type": "array",
                            "items": {
                                "$ref": "#/definitions/Project"
                            }
                        }
                    },
                    "default": {
                        "description": "Error",
                        "schema": {
                            "$ref": "#/definitions/Error"
                        }
                    }
                }
            }
        },
        "/crud/pid": {
            "get": {
                "summary": "Open a project",
                "description": "any description\n",
                "parameters": [
                    {
                        "name": "pid",
                        "in": "query",
                        "description": "Project ID",
                        "required": true,
                        "type": "string"
                    }
                ],
                "tags": [
                    "Project"
                ],
                "responses": {
                    "200": {
                        "description": "any description\n",
                        "schema": {
                            "type": "array",
                            "items": {
                                "$ref": "#/definitions/Project"
                            }
                        }
                    },
                    "default": {
                        "description": "Unexpected error",
                        "schema": {
                            "$ref": "#/definitions/Error"
                        }
                    }
                }
            }
        }
    },
    "definitions": {
        "Project": {
            "properties": {
                "_id": {
                    "type": "string",
                    "description": "Unique identifier setted by nedb.\n"
                },
                "pid": {
                    "type": "string",
                    "description": "Description of product."
                },
                "name": {
                    "type": "string",
                    "description": "Display name of product."
                },
                "path": {
                    "type": "string",
                    "description": "Capacity of product. For example, 4 people."
                }
            }
        },
        "Error": {
            "properties": {
                "code": {
                    "type": "integer",
                    "format": "int32"
                },
                "message": {
                    "type": "string"
                },
                "fields": {
                    "type": "string"
                }
            }
        }
    }
}
```
