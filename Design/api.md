# API Design

When designing APIs, representing all entity IDs as links may help to decouple the client from the server. I imagine the client could probably use a very generic request builder in such cases (see Hydra and [API Platform](https://api-platform.org)

Using an API for applications that can be accessed without authentication makes for endpoints that contain significant technical debt. If data is public it may as well be loaded via PHP templates, which will guarantee Google can access it. If Javascript behaviour is necessary then AJAX can be used.

GraphQL comes into its own for more complex APIs where you need to fetch data through several layers of related data, e.g. a hasManyThrough relation (things like comments with likes and votes and quiz builders spring to mind). For fairly flat APIs it adds less value. GraphQL can also be more flexible for changing client requirements.
