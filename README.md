Building the NordVPN Docker image

After you have set up the environment in Docker, make sure you’re in the same directory you have just created, which stores the Dockerfile. Once you’re certain you’re in the correct directory, you can proceed with building the NordVPN Docker image by following these steps:

    Build the image with this command (add your desired image name):

    sudo docker build -t <image name> .



Note: Do not forget the dot at the end of the command line.

Run the image:

sudo docker run -it --hostname mycontainer --cap-add=NET_ADMIN --sysctl net.ipv6.conf.all.disable_ipv6=0 <image name>



Explanation:
-it - instructs Docker to allocate a pseudo-TTY connected to the container’s stdin; creating an interactive bash shell in the container;
--cap-add - needed to successfully run the NordVPN Daemon and connect to our servers;
--sysctl net.ipv6.conf.all.disable_ipv6=0 - disables IPv6 traffic on Linux for the NordVPN container, making sure that there are no leaks after connecting to our servers.
--hostname - the hostname for your container. The flag should be used to prevent Meshnet hostname from changing after restarting the Docker container.

Login to NordVPN using a token method:

nordvpn login --token <your token>

After the steps are done, you have successfully set up NordVPN Docker image.

For more detailed information on how to use Docker, check the Docker documentation.
