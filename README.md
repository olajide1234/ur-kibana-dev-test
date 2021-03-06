# ur-kibana-dev-test
A simple test for UR Kibana devs (estimated time 6 - 8 hours)

**Overview:**  
 1. Start a new Kibana project 
 2. Bootstrap a new plugin 
 3. Convert plugin into a simple note taking application using React

**Detailed instructions:**  

 1. Download Kibana 7.9.0 from [https://github.com/elastic/kibana/archive/v7.9.0.zip](https://github.com/elastic/kibana/archive/v7.9.0.zip)
    (425MB)
2. Initialise the Kibana folder as a Git repository and
    commit the entire project to master, otherwise dependency install
    might fail
3.  Spin up a new Elasticsearch service using the provided Docker-compose file (762MB)
4. Update Kibana config
    (`your-path/kibana-7.9.0/config/kibana.yml`) with the following
    settings:   `elasticsearch.hosts : [your-elasticsearch-url]` 
  5. Install all dependencies in Kibana with `yarn kbn bootstrap` 
  6. Bootstrap a new plugin development with `node scripts/generate_plugin my_plugin_name`.  Create plugin in default
    plugin folder (`/plugin`); make sure to select ‘Yes’ when asked to
    generate an app component and server API. Other options can be ‘No’   
  7. Start Kibana with `yarn start --oss` (You can skip loading sample data)
  8. Scroll to the bottom of left panel in Kibana to see your new plugin   
  9. Edit the plugin component file (`your-path/kibana 7.9.0/plugins/my_plugin_name/public/components/app.tsx`)
    to transform the plugin into a simple single-page note taking app

    - The note taking app should use the Elastic EUI library (https://elastic.github.io/eui)
    - Notes should always have a title and text content
    - All submitted notes should be displayed on the page in a card tile format
    - Please save notes on the Elasticsearch service and retrieve same to display on the app
    - You can connect to Elasticsearch on the server-side with the 'Elasticsearch' node module already present in Kibana. No need to use internal Kibana methods
    - No need to implement authentication for Elasticsearch or Kibana

  10. Zip your plugin file (`your-path/kibana-7.9.0/plugins/my_plugin_name`) and submit along with screenshots of the app for review
  
  **Bonus:** 
  
    - Re-implement the note taking app in a simple ‘Create-react-app’ project and implement a maximum of 5 unit tests, preferably using React Testing Library
    (https://testing-library.com/docs/react-testing-library/example-intro).
    Zip the project without `node-modules` and submit for review
    - Connect Kibana to Elasticsearch using internal methods e.g. `callAsCurrentUser` 

**Useful references:**  
1. Elasticsearch setup: 
    -  https://medium.com/@alexdimango/elasticsearch-with-docker-in-five-minutes-401f0c5e403d;
    -  https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-docker.html
2. Guide to developing Kibana plugins [https://www.elastic.co/guide/en/kibana/7.9/external-plugin-development.html](https://www.elastic.co/guide/en/kibana/7.9/external-plugin-development.html)  
3. Connecting Node to Elasticsearch: https://qbox.io/blog/integrating-elasticsearch-into-node-js-application
4. Follow Kibana style guide as much as possible (however, do not let it hinder you, just add a comment where you avoid the styleguide on purpose): (`your-path/kibana-7.9.0/STYLEGUIDE.md`)
