# GraphQL vs REST API



# 2 The problem with REST

## 2.1 Overfetching

In the context of retrieving specific user information through a REST API, a GET request to /users/1234 is typically employed. However, this request often yields more data than required, encompassing details such as gender, birthdate, phone number, and other extraneous information. This phenomenon is commonly referred to as overfetching.

Overfetching poses several challenges. Firstly, it increases the payload size of the response, resulting in a larger volume of data being transferred over the network. Consequently, this surplus data consumes additional bandwidth and contributes to slower request processing times.

Moreover, the issue of overfetching can exacerbate when the user endpoint is designed to retrieve related data from associated tables. For instance, retrieving information about a user might inadvertently trigger the retrieval of all orders made by that user. As a result, not only is the user table accessed, but additional unnecessary data from the order table is also fetched. This compounded overfetching scenario amplifies the overhead associated with data retrieval, further compromising performance and efficiency.

The adverse consequences of overfetching highlight the importance of optimizing API design to mitigate these challenges. By tailoring the response to include only the required attributes, such as the user's name and email, unnecessary data can be avoided. Implementing strategies like selective field inclusion or utilizing separate endpoints for specific data needs can help address overfetching issues. Such measures minimize payload size, streamline network communication, and enhance overall system performance. [[1]](https://www.freecodecamp.org/news/graphql-vs-rest-api/)

## 2.2 Thight coupling

While utilizing custom controllers in a RESTful architecture may seem appealing at first, it is important to acknowledge a significant drawback associated with this approach. The primary concern stems from the tight coupling that emerges between the front-end view and the back-end controller, which introduces challenges when adapting to changes on the client side and restricts flexibility.

As Software Engineers, we are well aware of the dynamic nature of requirements, which often undergo frequent modifications. In the case of a custom controller, such as the one used in GET /user-experience, the data returned depends on the specific needs of the front-end view, such as retrieving the user's name and current role. Consequently, when a requirement changes, both the client and server must be refactored.

To illustrate this issue, let's consider a scenario where, after a considerable period of time, the requirement shifts, and instead of displaying experience data, the UI needs to present a user's last transaction information. This change necessitates adjustments in the front-end layer. Additionally, on the server side, the custom controller must be refactored to handle the new data (e.g., modifying the data sent, routes, etc.). Alternatively, a new controller could be created to preserve the functionality of the existing one.

Essentially, modifications in client requirements significantly impact the data to be returned by the server, creating a tight coupling between the front-end and back-end components. This tight coupling means that any alterations on the server side, even if solely related to the data format or structure, require changes to be made in both the front end and back end.

Ideally, it would be preferable to minimize server-side modifications and instead focus on adapting the front-end layer to accommodate changing requirements. By decoupling the front-end and back-end components to a greater extent, flexibility and maintainability can be improved. This can be achieved through strategies such as implementing a more generic API that caters to various client needs or adopting a microservices architecture, where each service has its own well-defined API, allowing independent evolution and reducing the impact of client-side changes on the server.[[1]](https://www.freecodecamp.org/news/graphql-vs-rest-api/) [[2]](https://krify.co/advantages-and-disadvantages-of-rest-api/)

# 3 What does GraphQL solve?

## 3.1 Single call

One of the key distinctions between GraphQL and REST lies in their approach to data retrieval. While REST revolves around individual endpoints, necessitating the combination of multiple endpoints to gather all the required data, GraphQL focuses on the specific task at hand, enabling developers to request the necessary data through a single API call.

In a REST architecture, data is typically exposed through specific endpoints, each corresponding to a particular resource or entity. To retrieve related data or construct a comprehensive view, developers often need to make multiple requests to different endpoints and then manually combine the obtained data on the client side. This process can become cumbersome and result in overfetching or underfetching of data.

On the other hand, GraphQL provides a more efficient and flexible approach to data retrieval. With GraphQL, developers can define a single query that specifies the exact data requirements for a given task. This query is sent to the GraphQL server, which then responds with precisely the requested data, eliminating the need for multiple requests. The client has control over the data it receives, receiving only the fields explicitly requested and avoiding unnecessary data transfer.

The advantages of GraphQL's approach are especially pronounced in scenarios where the client requires customized or varying data sets. By allowing clients to precisely define their data needs and reducing the number of round trips to the server, GraphQL offers improved efficiency, reduced network overhead, and enhanced developer productivity. [[3]](https://dzone.com/articles/graphql-core-features-architecture-pros-and-cons)

## 3.2 Client decides the data

In REST API documentation, individual endpoints, their functionalities, and the parameters that developers can utilize are typically described. While this documentation provides insights into the available resources, it offers limited control over the response structure and content. As a result, REST APIs are prone to returning surplus or inadequate data.

On the other hand, GraphQL APIs offer greater flexibility and customization options for data retrieval. The GraphQL schema serves as a comprehensive reference, describing the data types, fields, and their relationships. This empowers developers to tailor their requests, specifying the precise information they require. By defining the fields and relationships in their queries, developers can optimize data retrieval, eliminating unnecessary data and reducing the payload size. Consequently, GraphQL enables the retrieval of the exact data needed in a single API call, eliminating the need for additional requests and enhancing overall efficiency. [[4]](https://stablekernel.com/article/advantages-and-disadvantages-of-graphql/)

# 4 The drawbacks of GraphQL

## 4.1 High learning curve

Building a GraphQL API can indeed be more challenging to grasp initially compared to developing a REST API. Several factors contribute to this disparity, including the relative maturity and widespread adoption of REST, which has fostered a larger community and better code support.

REST has been around for a longer time and has gained significant popularity, resulting in extensive documentation, tutorials, and readily available code examples. The vast community surrounding REST provides valuable resources and support for developers, making it relatively easier to understand and implement RESTful APIs.

In contrast, GraphQL is a relatively newer technology that introduces a different paradigm for API development. Its unique concepts, such as schema definition, resolvers, and the query language itself, require developers to familiarize themselves with new concepts and patterns. Consequently, the learning curve for GraphQL may initially appear steeper.

However, it is worth noting that the learning curve for GraphQL is not excessively high. Once developers become accustomed to its principles and gain practical experience, they often find it easier to work with and integrate into their preferred web frameworks. As familiarity grows, developers can leverage the flexibility and power of GraphQL to efficiently retrieve data, resolve complex queries, and optimize API responses.

Moreover, GraphQL's ability to request precisely the required data and avoid over-fetching or under-fetching can result in more streamlined and efficient data retrieval compared to REST APIs. This capability, coupled with advancements in GraphQL tooling and growing community support, contributes to a smoother adoption and implementation process.

## 4.2 Caching

REST APIs offer the advantage of configuring a web cache to match specific URL patterns, HTTP methods, or individual resources. This caching mechanism helps reduce the load on the web server by serving cached responses instead of making repetitive requests.

In contrast, GraphQL typically relies on a single endpoint, often an HTTP POST endpoint, where all queries are sent. Due to the dynamic nature of GraphQL queries, it becomes more challenging to implement traditional caching strategies. Each GraphQL query can be unique, making it harder to cache and reuse responses. [[5]](https://blog.logrocket.com/graphql-vs-rest-api-why-you-shouldnt-use-graphql/#web-cache)

# When to use GraphQL

While GraphQL offers significant advantages, it may not always be the optimal choice, particularly when developing small and straightforward APIs with only a few endpoints. In such cases, REST may prove simpler and more suitable, preventing unnecessary code complexity.

However, when constructing larger APIs that involve numerous interconnected data tables, the limitations of REST can become more prominent, and GraphQL's benefits begin to outweigh its drawbacks. GraphQL excels in scenarios where data is spread across multiple tables or resources, as it allows for efficient and precise data retrieval by requesting only the required fields and relationships.

Additionally, GraphQL possesses a self-documenting nature, which proves advantageous when project requirements inevitably change over time. By adjusting the GraphQL schema, developers can readily accommodate these modifications, minimizing the need for extensive backend changes. Typically, updating the frontend code to align with the new schema is sufficient, reducing development time and effort.

It's important to assess the specific needs and complexity of the API being developed to determine whether GraphQL or REST is the most suitable choice. Smaller, simpler APIs may benefit from the straightforwardness and ease of REST, whereas larger APIs with complex data structures can leverage GraphQL's capabilities for efficient data retrieval and schema evolution.

# 5 Conclusion

In conclusion, the choice between GraphQL and REST depends on the specific requirements and complexities of the API being developed. While REST is suitable for small and simple APIs, GraphQL excels in larger projects with complex data structures and multiple interconnected tables. REST APIs may suffer from overfetching and tight coupling, resulting in inefficient data transfer and difficulties in adapting to changing client needs. On the other hand, GraphQL solves these challenges by allowing precise data retrieval in a single request and providing flexibility in tailoring requests.

Although GraphQL has a higher learning curve initially, it offers benefits such as efficient data retrieval, schema evolution, and self-documentation. As developers become familiar with GraphQL, they can leverage its power to optimize API responses and simplify data retrieval compared to REST. However, caching can be more challenging with GraphQL due to the dynamic nature of queries. Therefore, the choice between GraphQL and REST should be based on the size, complexity, and anticipated changes of the API. While REST is suitable for simpler APIs, GraphQL's advantages become more prominent in larger projects where precise data retrieval, flexibility, and schema evolution are crucial.

# 6 Sources

[1] Source: "GraphQL vs REST API – Which Should You Use for Back End API Development?", freecodecamp.org, https://www.freecodecamp.org/news/graphql-vs-rest-api/

[2] Source: "Advantages and Disadvantages of REST API", krify.co, https://krify.co/advantages-and-disadvantages-of-rest-api/

[3] Source: "GraphQL: Core Features, Architecture, Pros, and Cons", dzone.com, https://dzone.com/articles/graphql-core-features-architecture-pros-and-cons

[4] Source: "Advantages and Disadvantages of GraphQL", stablekernel.com, https://stablekernel.com/article/advantages-and-disadvantages-of-graphql/

[5] Source: "GraphQL vs. REST APIs: Why you shouldn’t use GraphQL", logrocket.com, https://blog.logrocket.com/graphql-vs-rest-api-why-you-shouldnt-use-graphql/#graphql-tasks-complex

# 7 Acknowledgements

This project was made possible with the assistance of ChatGPT, an AI language model developed by OpenAI.
