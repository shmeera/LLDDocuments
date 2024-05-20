# API Concepts

## 1. API Versioning

**What it is:** A strategy to manage changes in an API while ensuring compatibility with existing client applications.

**Why it's important:** Allows you to evolve your API without breaking existing integrations.

**Common approaches:**
- URI Path Versioning: Version number in the URL path (e.g., `/api/v1/users`).
- Request Parameter Versioning: Version number as a query parameter (e.g., `/api/users?version=v1`).
- Custom Header Versioning: Version number in a custom HTTP header (e.g., `X-API-Version: v1`).
- Media Type Versioning: Content negotiation based on Accept header (e.g., `Accept: application/json;version=v1`).

**Choosing the right approach:** Consider factors like clarity, flexibility, complexity, and maintainability.

## 2. Swagger

**What it is:** An open-standard framework for describing, documenting, and consuming RESTful APIs.

**Benefits:**
- Standardized documentation: Improves developer experience and API discoverability.
- Interactive documentation: Allows developers to test and interact with the API directly from the documentation.
- Code generation: Can generate client-side code for various languages based on the Swagger specification.

**Tools:** Swagger UI, Swagger Editor, various language-specific libraries.

## 3. RPC (Remote Procedure Call)

**What it is:** A mechanism for creating distributed applications where a client can execute a procedure on a remote server as if it were a local call.

**How it works:**
1. Client marshals method call and arguments into a message.
2. Message is sent over a network to the server.
3. Server unmarshals the message, executes the method, and marshals the return value.
4. Return value message is sent back to the client and unmarshaled.

**Advantages:**
- Language independence: Clients and servers can be written in different languages.
- Procedural abstraction: Hides network details from the developer.

**Disadvantages:**
- Performance overhead: Marshaling/unmarshaling and network communication can be slow.
- Tight coupling: Changes on the server can break client code.

## 4. Protocol Buffers (Protobufs)

**What they are:** A language-neutral, platform-neutral mechanism for serializing structured data (efficient message serialization format).

**Benefits:**
- Compactness: Smaller message sizes compared to JSON or XML.
- Performance: Faster serialization and deserialization due to a compiled format.
- Language neutrality: Can be used across different programming languages with generated code.
- Schema evolution: Forward and backward compatibility features for handling changes in message schema.

**Uses:**
- API request/response messages (RPC alternatives).
- Data interchange between microservices.
- Configuration files.