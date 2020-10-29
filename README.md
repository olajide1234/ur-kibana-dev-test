# ur-kibana-dev-test
A simple test for UR Kibana devs

**Overview:**  
 1.  Start a new Kibana project 
 2. Bootstrap a new plugin 
 3. Convert plugin into a simple note taking application using React

**Detailed instructions:**  

 1. Download Kibana 7.9.0 from
    [https://github.com/elastic/kibana/releases/tag/v7.9.0](https://github.com/elastic/kibana/releases/tag/v7.9.0)
    or
    [https://github.com/elastic/kibana/archive/v7.9.0.zip](https://github.com/elastic/kibana/archive/v7.9.0.zip)
    (425MB)
2. Initialise the Kibana folder as a Git repository and
    commit the entire project to master, otherwise dependency install
    might fail.
3. Update Kibana config
    (`your-path/kibana-7.9.0/config/kibana.yml`) with the following
    settings (make new credentials here if connection fails: cloud.elastic.co):   `elasticsearch.hosts : https://0ee03e5d00f14336a64734978ec2aa10.eastus2.azure.elastic-cloud.com:9243/`
    `elasticsearch.username: "test"`  
     `elasticsearch.password:
    "test12"`   
  4. Install all dependencies with `yarn kbn bootstrap` 
  5. Bootstrap a new plugin development with `node scripts/generate_plugin my_plugin_name`.  Create plugin in default
    plugin folder (`/plugin`); make sure to select ‘Yes’ when asked to
    generate an app component. Other options can be ‘No’’.   
  6. Start Kibana with `yarn start` 
  7. Login with `Username: ‘test’, Password: ‘test12’` 
  8. Scroll to the bottom of left panel to see your new plugin   
  9. Edit the plugin component file (`your-path/kibana 7.9.0/plugins/my_plugin_name/public/components/app.tsx`)
    to transform the plugin into a simple note taking app. The note
    taking app should use the Elastic EUI library
    ([https://elastic.github.io/eui](https://elastic.github.io/eui)).
    Notes should always have a title and text content. All submitted
    notes should be displayed on the page in a card tile format. No need
    to store notes on a server, notes can be stored in web cache and can
    erase on refresh. Displayed notes should show date and time of
    creation.   
  10. Zip your plugin file (`your-path/kibana-7.9.0/plugins/my_plugin_name`) and submit     	along with screenshots of the app for review.
  
  **Bonus:**   Re-implement the note taking app in a simple ‘Create-react-app’ project and implement a maximum of 5 unit tests, preferably using React Testing Library
    ([https://testing-library.com/docs/react-testing-library/example-intro](https://testing-library.com/docs/react-testing-library/example-intro)).
    Zip the project without `node-modules` and submit for review.

**Useful references:**  
1. Guide to developing Kibana plugins [https://www.elastic.co/guide/en/kibana/7.9/external-plugin-development.html](https://www.elastic.co/guide/en/kibana/7.9/external-plugin-development.html)  
2. Follow Kibana style guide as much as possible (however, do not let it hinder you, just add a comment where you avoid the styleguide on purpose): (`your-path/kibana-7.9.0/STYLEGUIDE.md`)
