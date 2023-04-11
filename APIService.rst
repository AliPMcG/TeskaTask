API Service
=========

The ASAB API Service allows you to make updates to your ASAB Microservice via API calls. The updates that you can make include:

1. Add a dictionary of errors to the list of dictionaries of errors requiring attention
2. Remove a dictionary of errors requiring attention
3. Initialize the API Service into a Web container
4. Initialize the API Service into a Zookeeper container
    
Add a dictionary of errors to the list of dictionaries of errors requiring attention
-------------------

To add a dictionary of errors that require attention, use the ApiService.attention_required method, with the dictionary of errors as the argument.

For example:

errors_requiring_attention = {1:"error 1", 2:"error 2", 3:"error 3"}
ApiService.attention_required(errors_requiring_attention)

# the method returns an att_id for the dictionary of errors

Remove a dictionary of errors requiring attention
-------------------

To remove a dictionary of errors requiring attention, use the ApiService.remove_attention method, with the app_id of the dictionary you wish to remove as the argument.

For example:

ApiService.remove_attention(1)

# this removes the dictionary of errors with the app_id "1" from the list of dictionaries of errors requiring attention

Initialize the API Service into a Web container
-------------------

To initialize the API Service into a web container, use the ApiService.initialize_web(webcontainer) method. If the argument is left empty, the method initalizes the Service into a default Webcontainer.

Example specifying Web container:

websvc = self.App.get_service("asab.WebService")
webcontainer = asab.web.WebContainer(websvc, 'web')
ApiService.initialize_web(webcontainer)

Example using default Web container:

ApiService.initialize_web()

Initialize the API Service into a Zookeeper container
-------------------

To initialize the API Service into a web container, use the ApiService.initialize_web(webcontainer) method. Similar to the Web container method, if the argument is left empty, the method initalizes the Service into a default Zookeeper container.

Example specifying Zookeeper container:

zksvc = self.App.get_service("asab.ZooKeeperService")
zoocontainer = ZooKeeperContainer(zksvc, "mycontainer")
ApiService.initialize_zookeeper(zoocontainer)

Example using default Web container:

ApiService.initialize_zookeeper()
