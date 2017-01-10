# Ruby
## Rails

Make sure you have Rails:
```
gem install rails
```

- Create lti_settings.yml from the template lti_settings.yml.template
    - It's located in the config folder
- Also create secrets.yml from the secrets.yml.template file
    - In the config folder as well
    - You can use 'rails secret' to generate a key

The server can be run by navigating to the root of the project and running:
```
bin/rails server
```

Here's the commadn to create a DB, if you need it. Rails does a lot of magic,
so it will generate files that it needs.
```
rake db:create
```

To generate tables for your db:
```
rails generate scaffold Test user:string user_id:int
```
This will create a model and a migration file that will create a db table that
corresponds to it, a controller, and a few views.

Go ahead and migrate to create them:
```
rake db:migrate
```

Test your xml and adding your LTI. Rails does a lot of black magic!

# Install LTI
- Have the XML, consumer key, and secret ready.
    - You can use the [XML Config Builder](https://www.edu-apps.org/build_xml.html) to build XML.
- Navigate to the course that you would like the LTI to be added to. Click Settings in the course navigation bar. Then, select the Apps tab. Near the tabs on the right side, click 'View App Configurations'. It should lead to a page that lists what LTIs are inside the course. Click the button near the tabs that reads '+ App'.
- A modal should come up that allows you to customize how the app gets added. Change the configuration in the Configuration Type dropdown menu to 'By URL' or 'Paste XML' depending on how you have your LTI configured. If your LTI is publicly accessible, 'By URL' is recommended. From there, fill out the Name and Consumer Keys, and the Config URL or XML Configuration. Click Submit.
- Your LTI will appear depending on specifications in the XML. Currently, they get specified in the **options** tag within the **extensions** tag. Extensions can include these options:
    - Editor Button (visible from within any wiki page editor in Canvas)
    - Homework Submission (when a student is submitting content for an assignment)
    - Course Navigation (link on the lefthand nav)
    - Account Navigation (account-level navigation)
    - User Navigation (user profile)

**Note**: If you're using Canvas, your version might be finicky about SSL certificates. Keep HTTP/HTTPS in mind when creating your XML and while developing your project. Some browsers will disable non-SSL LTI content until you enable it through clicking a shield in the browser bar or something similar.