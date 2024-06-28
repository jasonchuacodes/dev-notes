```
In NestJs, the initial response of the request contained the user's password.
This isn't good practice so we used 'serialization'.

what is serialization?
```

Serialization is the process of converting an object instance into a format that can be easily stored or transmitted over a network. In the context of NestJS, serialization is used to transform an object into a plain JavaScript object (POJO) that can be safely sent as a response without exposing sensitive information.

In the case mentioned above, serialization is used to remove the user's password from the response object. This is typically done by defining a DTO (Data Transfer Object) that contains only the fields that should be included in the response. The DTO is then used to transform the user object into a plain JavaScript object that can be safely sent as a response.