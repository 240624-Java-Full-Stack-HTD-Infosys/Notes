# QC questions for Javalin

What is the Context object?
This is the object which represents the request and reponse objects. It is a wrapper around these two things. Context has an interface (a way to interact with it) that involves a number of overloaded methods to get/set values in reqesut/response. An API wrapped around these with an interface used to access the underlying mechanisms of each.

What is Jetty? A servlet container.

How do we "map" request handlers?
We register it with the Javalin object, passing two parameters:
 - The endpoint (URI path string)
 - The behavior, the handler, in this case with Javalin it is a lambda function (Java functional programming)
We use the methods to register: .get(), .post(), .put(), .delete(), etc.


How do we handle errors and exceptions in Javalin?
Also we can register error and exception handlers in a similar way: .error(), .exception()

How do we get headers from Javalin requests?
We use Context.header(String name) or similar methods to fetch the headers from the context object.

How do we get parameters from the request?
query params: ctx.queryParam(String name);
path params: ctx.pathParam(String name);

How do we set the reponse status code?
ctx.status(int code);

How do we get the JSON body from a request?
ctx.bodyAsClass()
"There is a method on the context opbject which will translate from the JSON body to a Java class."

How do we return a JSON resource representation?
ctx.json(Object obj)



