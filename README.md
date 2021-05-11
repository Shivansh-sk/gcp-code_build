# gcp-code_build
Continuous Deployment with Cloud Run

Cloud Build is a service that executes your builds on Google Cloud Platform's infrastructure. It can import source code from a variety of repositories or cloud storage spaces, execute a build to your specifications. 
Cloud Run is used to develop and deploy highly scalable containerized applications on a fully managed serverless platform.

##Setup Instructions
Follow these instructions to deploy the application on Google Cloud

###Cloud Build Setup
1. Upload the files to your repository.
2. Go to Cloud Build and click on **Triggers**. Now connect your repository to Cloud Build.
3. Create a trigger and choose your repository as the *Source* and the *Branch* you wish to build (here, main).  
![image](https://user-images.githubusercontent.com/59771258/117806639-36ca9d80-b278-11eb-8857-de25c6c0608f.png)

4. Go back to triggers and find the trigger you created and click on **RUN**.
4. Now go to **Settings** and make the status of Cloud Run to be *Enabled*
![image](https://user-images.githubusercontent.com/59771258/117807581-6fb74200-b279-11eb-9aee-b0ed010fe522.png)

###Cloud Run Setup
1. Go to Cloud Run and create a service. Choose the *Container image URL* we just created from Cloud Build
2. Under the **Configure how this service is triggered** --> **Authentication** choose the *Allow unauthenticated invocations* option as we are building a public website. 
![image](https://user-images.githubusercontent.com/59771258/117808626-be191080-b27a-11eb-8b81-2badcd58878e.png)

3. Click on Create.

The setup is complete and now we have to test the website.

Go back to your repository and we make a simple change to the *server.js* file to trigger the Cloud Build. Write anything withing the quotes and commit the file. 
`res.end('AWESOME- TFT')`

At the Cloud Build History, we can see that a build is in progess and after the build has been completed, it will provide with a service URL through which we can access the website. 
![image](https://user-images.githubusercontent.com/59771258/117809618-0127b380-b27c-11eb-9786-1054e1924177.png)

Browse to the URL and you will be able to see the website.
![image](https://user-images.githubusercontent.com/59771258/117809722-25839000-b27c-11eb-8cad-542b0bf52b88.png)


