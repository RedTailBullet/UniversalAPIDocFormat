# Universal API Documentation Format

This project is designed to develop an universal API documentation format for any kind of APIs.

## Basic idea

The basic idea behind this project is to produce an API format that can be easily understood by both human and program, and potentially enable the possibility of developing a full set of API development tools base on it.

One of the major consideration here is that this API format should not be used for REST API only, but for software API and GraphQL API as well.

## Glossary

Symbol or Word|Meaning|Example
---|---|---
"API"|Application programming interface.
`${}`|Indication of user defined parameters|`${version}`

## Understanding about APIs

### API identifier

Each API should have an identifier.

In Application API, the identifier is a string that can be used to identify an unique API or the name of the API. For example, in Java, a typical API name can be `org.scott.Profile.get`.

In REST API, the identifier is the path inside an URI which is used to identify a specific endpoint inside the server. For example, `/scott/profile`.

In GraphQL, the identifier of an API should be the name of the Graphql endpoint identifier. For example `userProfile`.

## Proposed format

First of all, the format should be based on the JSON format to enable easy understanding for both human and machine.

### Argument options object:

```JSON
{
  "min": 1.0,
  "max": 100.0,
  "default": "${default_value}",
  "length": 10,
  "transCase": "none"
}
```

1. `min` | `max`: The minimum and maximum limitation for the argument, only apply to number types input.
2. `default`: The default value for this argument. Can be of any type.
3. `length`: Length restriction for argument. Only apply to array like argument such as string.
4. `transCase`: Whether to transfer the case of the input and what case should it be. Only apply to string input.

### Argument object:

```JSON
{
  "type": "string",
  "optional": true,
  "options": "#Argument options object"
}
```

1. `type`: The type of this input, for example `string` or `int`.
2. `optional`: Whether this argument is optional.
3. `options`: An [ArgumentOptionsObject](#augument-options-object).

### Argument location object:

```JSON
{
  
}
```

```JSON
{
  "version": "${version_of_API_doc}",
  "name": "${name_of_API_doc}",
  "type": "${type_of_APIs_in_this_doc}",
  "APIs": {
    "${group_name_of_APIs}": {
      "${name_of_API}": {
        "identifier": "${identifier_of_API}",
        "inputs": {
          "body": {
            "argumentName": {
              "type": "${basic_type}",
              "optional": true,
              "options": {
              }
            }
          }
        }
      }
    }
  }
}
```