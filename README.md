# Azure_Container_Build_Task.ado
Use this Azure template for Container build task in Azure Devops Pipeline with the use of a Dockerfile.

## Parameters:

The pipeline requires the following parameters to be defined:


| Name  | Displayname | type | Default | Values | Opional/Required | Comments |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| Dockerfile | Dockerfile | string | Dockerfile | | Required | The path to the Dockerfile |
| dockerRegistryServiceConnection | Docker registry service connection | string | | | Optional | Specifies a Docker registry service connection |
| repository  | Container repository | string | | | Optional | The name of the repository within the container registry |
| tags | Tags | string |  | | Optional | The list of tags in separate lines. Tags are used while building and pushing the image to container registry |
| buildContext  | Build Context | string | '.' | | Optional | The path to the build context |

--------------------------------------------------------------------------------------------------------------------------------------------------

These parameters provide multiple use case options for the template, enable/disable flags for the utilization of different templates as per the requirements.


## Use Cases

You can directly call a particular template as per the requirement. for example: 

  ```yaml
  # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name: your_username/Azure_Container_Build_Task.ado
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'

  steps:
  # passing the parameters
  - template: Azure_Container_Build_Task.yml
    parameters:
      Dockerfile: '${{parameters.Dockerfile}}'      
      dockerRegistryServiceConnection: '${{parameters.dockerRegistryServiceConnection}}'     
      repository: '${{parameters.repository}}'      
      buildContext: '${{parameters.buildContext}}'     
      tags: '${{parameters.tags}}'   
        
  
Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.
