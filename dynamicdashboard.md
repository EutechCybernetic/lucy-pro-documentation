

<a name='dyndashboards'></a>

# Dynamic Dashboards
All |instances| in Lucy have the option of presenting a dynamic dashboard to users.
Dynamic dashboards are a collection of weblets that are specific to or related to a given model.

The dashboard is dynamically assembled by action sequences in the model and updates itself in real-time.

# Creating the dashboard
The dashboard is automatically enabled when the first weblet is added to it.
At that point, the model instance screen in iviva will show a dashboard tab as the first tab.

# Adding Weblets
Weblets can be added to the dashboard via action sequence logic. Use an |addweblet| block to trigger the addition of a weblet to the dashboard.

When the block executes, a weblet is added to the dashboard and all viewers of the dashboard will be dynamically updated to reflect the new weblet.

# Syncing the dashboard layout
You can choose to layout the weblets on the dashboards as you see fit. Your layout is specific to the user you have logged-in as. Other users will see the same instance dashboard in their own layout.
If you wish to share your layout with others, click the button to *Update All* dashboards at the top of the screen. This will cause all viewers of that instance dashboard to get your updated layout.
If a user happens to be viewing that dashboard at that time, they will get a notification on screen with an option to reload the dashboard layout to get the new update you have sent.