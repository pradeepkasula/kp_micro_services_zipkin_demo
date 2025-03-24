

**What is Logging & Tracing?**

Tracing : Tracing is a process of finding an execution path or a flow of multiple microservices to serve a request.

Logging : Logging is a process of admitting all log messages for a trace. These messages can be of any type such as DEBUG, INFO, WARN, ERROR etc.

Here, we will be implementing Logging and Tracing for multiple Microservices involved in serving one request. We also call it ‘Distributed Tracing and Logging’. Once it is implemented one time, then developer doesn’t need to check the code again to find the flow either for testing purpose or for debug purpose.

**What is Sleuth and Zipkin used for ?**

Sleuth 
Sleuth provides unique ids for the request flow. Further, the developer uses these ids to find out the flow of execution with the help of tools like Zipkin, ELK etc. Generally it has two ids : Trace id and Span Id. Trace Id is applicable for a complete flow. If the developer gets this Id, he/she can find the flow of execution in all microservices involved.

However, Span Id is applicable to the flow of one microservice. If the developer gets this Id, he/she can find the flow of execution in a particular microservice. Moreover, there is a concept of parent id which is applicable to a particular microservice like span id. During the flow of execution, span id of the previous microservice becomes the parent id of the next microservice as shown below.

Sleuth

Zipkin 
We use Zipkin in two parts : Zipkin Client and Zipkin Server. Zipkin Client contains Sampler which collects data from microservices with the help of Sleuth and provides it to the Zipkin Server. In order to utilize the benefits of both tools, we should always add Zipkin Client’s dependency along with Sleuth in every microservice.

However, there must be only one centralized Zipkin Server, which collects all data from Zipkin Client and display it as a UI. Hence, after making a request developer should look into Zipkin Server to find trace id, span id and even flow of execution. From here itself, Open Log files to check Log lines that are related to the current trace Id.
