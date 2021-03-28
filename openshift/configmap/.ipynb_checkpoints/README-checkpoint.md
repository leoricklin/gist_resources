# ConfigMaps

# Resources:

* CongMaps, Dev Guide, OC 3.9, https://docs.openshift.com/container-platform/3.9/dev_guide/configmaps.html


### How-to



* Create new Config Map: 
  * Web console > Resources > Config Maps, <img src="01.png" style="display:block;margin-left:0;height:200px;"/>
  * Click "Create Config Map" 
    * Name: Input the name of the config map
    * Key: Input the key. The key would be the file name under
    * Value: input the value. It woule be the content of the file.
    * Click "Create", <img src="02.png" style="display:block;margin-left:0;height:400px;"/>

* Modify Config Map
  * Click on any existing config map, <img src="03.png" style="display:block;margin-left:0;height:150px;"/>

* Apply Config Map: 
  * Click on any existing config map > click "Add to Application"
    * Select an application:
    * Add config map as volumn: input the mount path name, ex: /tmp/src. You could overwrite the path that alredy exists in the container.
    * The OpenShift will re-deploy the application. <img src="04.png" style="display:block;margin-left:0;height:300px;"/>

* Check the result
  * Web console > Applications > Deployments > choose the application
    * In "Configuration" tab you could find the mounted config maps. <img src="05.png" style="display:block;margin-left:0;height:400px;"/>
    * You can remove the mounted config maps in "Volumes" section.
  * Web console > Applications > Deployments > choose the latest deployment of the application > choose pods
    * Click the "Terminal" tab to open terminal, you could get the config map content from the file. <img src="06.png" style="display:block;margin-left:0;height:400px;"/>
