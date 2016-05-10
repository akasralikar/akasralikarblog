
Like other topics, I think the best way to understand the Model View Controller design pattern is to break it down into individual pieces, and then putting them together to see how they all work with each other.

Model – Starting off with the model component, this is where the application data resides. For example, if you have an invoicing application, the model files will store items such as the attributes for invoices, custom methods such as how an invoice relates to the rest of the application, along with other features such as database query scopes. The model should only be called by the controller and shouldn’t have any interaction with the view.

Controller – Controller files manage data flow for the application, they take in requests from the routing engine and coordinates how the rest of the application processes that request. For example, in a sample invoicing application if you go to a page where you can create a new invoice. The controller would register that request, pick out what view should be rendered, and call the model for any data that is needed for the page. In a well written application controller files should not contain very much complex logic.

View – Views should be the most straightforward component in an application. The view should simply render the template and display any data passed to it by the controller, it should not have any direct communication with the model, instead it should only communicate with the controller.

A few months ago I worked on writing some Rails curriculum for Learn.co, and they had a great analogy for understanding the Model View Controller design pattern:

Imagine the the MVC architecture is a restaurant. The model is the chef, the chef’s role is to get orders from the waiter and make the meals. The waiter is the controller, they take requests from the customer, informs the chef, and brings the meal back to the customer. Lastly the view is the table, it simply holds the meal, it doesn’t have to do any type of complex task besides simply being there.

So why is the Model View Controller design pattern important? Imagine if everyone built applications the way that they personally felt code should be created, if new developers started to work on a project, they would have no idea where to even find features, much less how to extend the functionality or fix bugs. With the Model View Controller design pattern a new developer can quickly find where the data files are, how the data flow works, and where to update the view pages.

I hope that you now have a more clear idea of how the Model View Controller design pattern works and how you can implement it in your applications.
