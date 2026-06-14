# KeystoneJS GraphQL API

KeystoneJS auto-generates a fully typed GraphQL API from its schema definition — every list defined in `keystone.ts` produces a standard set of queries and mutations without any manual resolver writing. The generated schema exposes single-item lookups, paginated list queries with cursor-based and offset pagination, count queries, and both singular and batch create/update/delete mutations for each list. The schema is extended with authentication operations (session management, password-based login, initial user creation) when the `@keystone-6/auth` package is enabled, and developers can add arbitrary custom queries and mutations via the `extendGraphqlSchema` configuration option.

The API also exposes a `keystone { adminMeta }` query tree that describes the entire Admin UI configuration — list metadata, field metadata, visibility settings, and action definitions — enabling headless Admin UI clients to be built without hardcoding schema knowledge. All query arguments support rich filtering (`AND`, `OR`, `NOT`, field-level operators such as `contains`, `startsWith`, `gte`, etc.), multi-field ordering, and `take`/`skip`/`cursor` pagination. Relationship fields accept nested create and connect operations, making it straightforward to manage related records in a single mutation.

Access control is enforced at the list and field level through Keystone's `access` and `ui` configuration — the GraphQL API respects these rules at runtime. Session tokens returned by `authenticateUserWithPassword` must be sent as a cookie; Keystone uses HTTP-only cookies for session management rather than Bearer tokens by default. The endpoint path is configurable but defaults to `/api/graphql` and also serves the GraphQL Playground in development mode.

**Endpoint:** https://your-keystone-app.example.com/api/graphql

**Documentation:** https://keystonejs.com/docs/graphql/overview

**References:**
- Documentation: https://keystonejs.com/docs/graphql/overview
- GettingStarted: https://keystonejs.com/docs/getting-started
- FilteringDocs: https://keystonejs.com/docs/graphql/filters
- AccessControl: https://keystonejs.com/docs/guides/auth-and-access-control
- ExtendGraphqlSchema: https://keystonejs.com/docs/config/config#extend-graphql-schema
- FieldTypes: https://keystonejs.com/docs/fields/overview
- GitHubSource: https://github.com/keystonejs/keystone
