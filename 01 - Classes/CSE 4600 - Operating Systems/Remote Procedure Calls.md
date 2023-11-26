2023/11/22 11:07
Status: #idea
Tags:

# Remote Procedure Calls (RPC)

  
Remote Procedure Calls (RPCs) are a powerful technique in client-server architecture, allowing a program on a client computer to execute code on a server as if it were a local procedure call. This approach simplifies the process of creating distributed, network-based applications. 

<mark style="background: #FFF3A3A6;">Stubs</mark> - client-side proxy for the different processes

## Key notes on RPCs for both client and server:

### For the Client:

1. **Abstraction of Complexity**: The client sees remote procedure calls as local function calls, abstracting the complexities of the network communication.
2. **Stub Generation**: The client uses a stub (a piece of code) that represents the server's procedure. This stub handles communication, serialization, and deserialization of data.
3. **Synchronous vs. Asynchronous Calls**: RPCs can be synchronous (blocking) where the client waits for the server to complete the procedure, or asynchronous, where the client proceeds without waiting for the response.
4. **Error Handling**: Clients must have mechanisms to handle potential errors like network failures, server unavailability, or execution errors on the server side.
5. **Security and Authentication**: The client should implement security measures to ensure data integrity and confidentiality during RPC calls.

### For the Server:

1. **Handling Multiple Requests**: Servers must efficiently handle multiple incoming RPC requests, often involving multi-threading or concurrent processing.
2. **Implementation of Procedures**: The server implements the actual procedures that are called by the client. These must be robust and secure.
3. **Stub and Skeleton Layer**: The server uses a skeleton layer that interfaces with server-side procedures. It receives requests from client stubs, unpacks them, and calls the appropriate server procedures.
4. **Resource Management**: Managing resources effectively is critical, especially in handling concurrent RPCs and maintaining performance and stability.
5. **Logging and Monitoring**: Implementing logging and monitoring mechanisms to track RPC calls, performance metrics, and potential issues for debugging and optimization.





---
# References

- [[Little & Big Endian]]
- 