##Group Task
Goal:
To run this static webpage on an Azure VM and serve the webpage using a webserver like Nginx or Apache:

Pre-requisites:
- An Azure Account (Feel free to also try this on AWS.)
- Knwoledge of Virtual Machine
- Knowledge of Linux CLI, Networking and DNS
- Knowledge of Git and Nginx
- Basic Understanding of Docker

Steps:
1. Setup a Virtual Machine (Preferably an Ubuntu based machine). Note: The Network Group attached to the VM needs to allow, HTTP, HTTPS from anywhere and SSH as well from at least your machine at the very basic.
2. SSH into your Azure VM using your preferred SSH client.
3. Install Dockerand Git on the VM by running the following command:
    ```
    sudo apt-get update
    sudo apt-get install docker.io
    sudo apt install git-all
    ```
4. Once installed next will be to clone the repository below by running the command:
    ```
    git clone https://github.com/COILS-Tech/static-webpage-task-2.git
    ```
5. Next you change into the directory to see your files and open it for editing(if you want to be geekiee) or just proceed with the deployment:
    ```
    cd static-webpage-task-2
    ```
6. Once you are within the "static-webpage-task-2" directory, you may want to verify the files in there by running:
    ```
    ls -ll

    cat Dockerfile
    ```

    This will list all the files you have in there and the cat command will show you the content of the Dockerfile so you are sure its not empty. Once that is confirmed, you can then go to the next step

7. Build the docker image.

    ```
    docker build -t myapp .
    ````

    NOTE: Take not of the "." after my-app. It must be included else your image will not build and you won't be able to run the next command

8. Run the container in a detached mode and map the port on the server to port 80 inside the container:
    ```
    docker run -d -p 80:80 myapp
    ```
    This command maps port 80 of the Azure VM to port 80 of the Docker container.

9. Access your static webpage by navigating to the public IP address of your Azure VM in a web browser.

10. Configure a DNS name for it on Azure and map it to the IP address of the VM 

That's it! Your static webpage should now be running on your Azure VM using Docker.



TASK 3
Deploy this App in a Web App (Individual Task)

- Setup a Web App using ARM template and deploy the above web page inside it and ensure that the Web Page is available.
- Modify the index.html file located in `/html/index.html` with your details: Name, username and email on your own named branch and deploy that to your web app.