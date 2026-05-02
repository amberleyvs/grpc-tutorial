## Reflection

**1. What are the key differences between unary, server streaming, and bi-directional streaming RPC methods, and in what scenarios would each be most suitable?**  
Unary means one request and one response, so it works well for simple tasks like login or payment. Server streaming means one request but many responses, which is useful when the data is large, like transaction history. Bidirectional streaming lets both sides send messages at the same time, so it is good for real-time uses like chat.  

---

**2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?**  
Security in gRPC includes checking who the user is, what they are allowed to do, and protecting the data. Authentication makes sure the user is real. Authorization controls what they can access. Encryption keeps the data safe while it is being sent. gRPC already supports secure communication to help with this. 

---

**3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications?**  
Bidirectional streaming is harder to manage because both sides send messages at the same time. You need to handle delays, lost connections, and make sure messages arrive in the right order. This becomes important in apps like chat where messages should feel instant and correct. 

---

**4. What are the advantages and disadvantages of using `tokio_stream::wrappers::ReceiverStream` for streaming responses in Rust gRPC services?**  
`ReceiverStream` helps send messages step by step to the client and works well with async code in Rust. It makes streaming easier to build. However, you still need to manage how messages are sent. If not handled well, it can cause problems like too much memory usage or lost messages.  

---

**5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity?**  
The code can be organized by separating parts like service logic, data, and setup into different modules. Using the same protobuf file for both client and server also keeps things consistent. This makes the code easier to understand, reuse, and update later. 

---

**6. In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic?**  
A more complete payment system should check the input, confirm the user has enough balance, and handle errors properly. It may also need to connect to a database or another service. Adding logs and retry steps can help make it more reliable.  

---

**7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems?**  
gRPC helps systems communicate faster and more efficiently. It works well with microservices and supports many programming languages, so different systems can work together easily. However, it is not always the best choice for browser-based apps. 

---

**8. What are the advantages and disadvantages of using HTTP/2 compared to HTTP/1.1 or WebSocket?**  
HTTP/2 is faster because it can handle many requests at once on one connection, which reduces waiting time. HTTP/1.1 is simpler and more widely used. WebSocket is good for real-time communication, but it needs more setup compared to gRPC.  

---

**9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?**  
REST works by sending a request and waiting for a reply each time, which can be slow for real-time updates. gRPC streaming keeps the connection open so data can be sent continuously. This makes it faster and better for real-time features like chat.  

---

**10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers?**  
Protocol Buffers require both client and server to follow the same data format. This makes communication clear and reduces mistakes. It also allows automatic code generation. However, it needs extra setup and is less flexible than formats like JSON.