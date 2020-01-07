## Data Visualization Scope of Work

The goal of this project is to present SendGrid API data in an accessible and readable visual format. Development data is available at two end points:

`https://api.webhookrelay.io/`

This endpoint provides all of the data available for the project. Each row of data includes a date, a provider and a series of `email events` as provided by the SendGrid API with the number of that event type for the day/provider. 

`https://api.webhookrelay.io/show?user-id=1&prov=aol`

This endpoint will allow for query parameters to be entered that include our development `user-id=1` and the provider string `prov=aol`. Querying the endpoint provided as shown above will return all of the data for the AOL email provider. For development purposes, we will only be using the `user-id=1` but the `user-id` and the `prov=""` should be dynamic for a production usecase.  

The list of providers in the sample data set: 

```
AOL, AT&T ("AT\u0026T"), BigPond, Charter, Comcast, Cox, Dream Host, EarthLink, Facebook, GMX, Gmail, GoDaddy, Hotmail, Libero, Mail.Ru, MessageLabs, Microsoft Forefront, Microsoft Hosted Exchange, Microsoft Outlook Live, Optus, Orange, Other, Postini, Prodigy, Rackspace, RoadRunner, Shaw, US Government, US Military, University, Verizon, WEB.DE, Yahoo, Yandex, ZohoMail, free.fr, iCloud
```

Our data visualization engine will need to query the database on a per user basis. Keep these variables in mind while developing the visualization dashboard. 

Here is an example of a visualization I created years ago using Ruby on Rails and HighCharts. On the left hand side there is a list of the providers. When a provider or group of providers are selected, the graphs populate in the body of the page with each providers data displayed as a line chart. The data can be filtered by `event type` using the key on the right side of the chart. The time series charts are also dynamic using the slider at the bottom. The time range can be adjusted and HighCharts does the work of scaling the graph for us. 

![Example](https://camo.githubusercontent.com/8b305889af926a5ae55c219716e0fb65f3bbcc5d/68747470733a2f2f73332d75732d776573742d312e616d617a6f6e6177732e636f6d2f73672d73746174732d6173736574732f53696d706c794d61696c5374617469737469637350726f7669646572732e706e67)


The final product should include a web server/service that is routable and listening on port 8080. The controller should be able to accept a User ID, make a database call, retreive the data for that user, then display it in a usable, functional and appealing manner. This service will need to be containerized so please use a few outside dependancies as possible. Outside charting libraries are acceptable. 

Requirements - 

- When a user visits the dashboard they should see a list of the email providers pulled from the query using the user-id (in this case `1`)

- A user should be able to select one or more providers and a graph of each provider's data should appear in the body of the website

- Provider data should be searchable and filterable. A user should be able to scale the timeseries data for the graphs and filter event types. The graphs should be dynamic when this is done (Most major graphing libraries do this for us)

- A user should be able to add and remove providers from the webpage body. 

- The design of the dashboard should be pleasant but doesn't need to be perfect. This dashboard will be specific to SendGrid so we can use [SendGrid's style guide as a reference.](https://styleguide.sendgrid.com/index.html)

- Please use a common programming language(s) to fulfill these requirements (PHP, Python, Ruby). If you are unsure please ask. 