# Security

## Access Control

Role-based access control may not be the right choice when permission to act on an entity is defined by business rules (e.g. user owns the entity, entity is active, user has subscription) rather than user role

When I find myself checking two data points to permit an action, this is a clear sign that the database structure is wrong. E.g. if we are checking both a user’s role and that they have a valid subscription, this is bad. Consider giving subscriptions and roles permissions and then merging them when checking a user’s permissions

When creating permissions hierarchies, assume the general “view” permission provides the bare minimum, and then add permissions on top to extend the permission. E.g. have  a ‘view users’ permission for viewing active users and then a ‘view inactive users’ to provide additional permission to view inactive users as well. This is as opposed to providing “view all users” and then restricting that permission with “view all active users”. With the former method, we are applying the principle of least power and it makes checking easier because there are no permission overlaps to negotiate.

## API Security

In API driven applications, clients and servers should manage their permissions independently to prevent the server from being coupled to the client

~~Token based auth is preferred for APIs because it doesn’t cause problems if you attempt to store the session over multiple locations (e.g. a sharded database). Also you can offset the performance cost to the client for the most part. Finally, they keep your API stateless. However, it’s important to note that tokens are not necessarily more secure than session based authentication.~~ (See below)

According to Auth0, there is no truly secure way of persisting a stateless access token of any kind (JWT, OAuth2 access token, session token, whatever) in browser storage (localStorage or cookies) across HTTP requests. Their SDK uses an invisible iframe to re-run the request for the access token on every page refresh

Traditional stateful authentication using session IDs stored in a cookie is secure as long as http-only and secure flags are set, CSRF protection is implemented, and client requests are coming from the same domain as enforced by CSP

## Encryption and Hashing

UUIDs have several different types:

- Uuid1 is time-based
- Uuid3 is name-based (i.e. will always return the same UUID if name is the same) and md5 hashed
- Uuid4 is cryptographically random
- Uuid5 is name-based and SHA-1 hashed
