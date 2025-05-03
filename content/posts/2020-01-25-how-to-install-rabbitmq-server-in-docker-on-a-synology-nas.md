---
title: How to Install RabbitMQ Server in Docker on a Synology NAS

date: 2020-01-25T23:46:56+00:00
url: /how-to-install-rabbitmq-server-in-docker-on-a-synology-nas/
cover: 
  image: https://blogstouks01.z33.web.core.windows.net/2020/01/2020-01-13_21-25-45-1.png

categories:
  - Tech

---
One of the game-changing features of [Synology][1]&#8216;s NAS (Network-Attached Storage) devices is their ability to run [Docker][2], the industry-standard containerization technology. This opens up the possibility of running all kinds of applications on the NAS, turning them into home servers with boundless possibilities.

One of things I wanted to run on my own Synology NAS is [RabbitMQ][3], the popular open-source message broker. I intend to use this as the heart of a distributed home climate measuring project, with a bunch of low-cost Raspberry Pi devices sending regular sensor readings to a database, or directly to a real-time web application.

Here’s how to go about installing RabbitMQ on a Synology NAS, as of January 2020. The whole process should only take around 15-30 minutes at most.

First, open up Package Center and search for the free Third-Party Docker package. If it’s not already installed, go ahead and Install it, otherwise Open it.

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_20-48-59-3.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_20-48-59-3.png" alt="" /></a></figure>
</div>

Within the Docker package, we need to search the Registry for the rabbitmq image. Look for the image with the “Official Image” icon next to it, which should be near the top of the search results.

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_20-50-09-1.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_20-50-09-1.png" alt="" /></a></figure>
</div>

Choose a tag to install. I recommend selecting a recent build with the “management” suffix – these tags have the RabbitMQ management plugin installed and enabled by default, which is available on the standard management port of 15672.

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_20-51-02.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_20-51-02.png" alt="" /></a></figure>
</div>

After the Docker image has downloaded to the NAS, select it from the list of images on the Image tab, and click Launch to create a new container from that image.

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_20-52-08.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_20-52-08.png" alt="" /></a></figure>
</div>

Give the new container a suitable name (rabbitmq seems the obvious choice), and then click the Advanced settings button.

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_20-52-43.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_20-52-43.png" alt="" /></a></figure>
</div>

Check Enable auto-restart so that the container automatically restarts, should it stop for any reason.

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_20-53-11-1.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_20-53-11-1.png" alt="" /></a></figure>
</div>

Containers should generally be treated as being replaceable, with any data that you care about being kept outside of the container. To this end, create a folder on the NAS that can be used as a volume for the /var/lib/rabbitmq mount path. This ensures all the data from the RabbitMQ instance exists outside of the container itself and won’t be lost if the container needs to be destroyed and recreated for any reason (such as upgrading to a new version of RabbitMQ).  
I also suggest creating a blank RabbitMQ config file – rabbitmq.conf – and mounting this file to the path /etc/rabbitmq/rabbitmq.conf .

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_20-56-21.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_20-56-21.png" alt="" /></a></figure>
</div>

RabbitMQ with the management plugin enabled uses ports 4369, 5671, 5672, 15671, 15672 and 25672. There’s a low probability of these ports already being in use by other applications on the NAS, so map those container ports to the same local ports.

[<img loading="lazy" decoding="async" width="1024" height="862" src="https://blogstouks01.z33.web.core.windows.net/2023/08/1_2020-01-13_20-57-55-1024x862.png" alt="" class="wp-image-8147" srcset="https://blogstouks01.z33.web.core.windows.net/2023/08/1_2020-01-13_20-57-55-1024x862.png 1024w, https://blogstouks01.z33.web.core.windows.net/2023/08/1_2020-01-13_20-57-55-300x252.png 300w, https://blogstouks01.z33.web.core.windows.net/2023/08/1_2020-01-13_20-57-55-768x646.png 768w, https://blogstouks01.z33.web.core.windows.net/2023/08/1_2020-01-13_20-57-55.png 1181w" sizes="auto, (max-width: 1024px) 100vw, 1024px" />][4]</figure> 

Check the Environment variables tab. The defaults should be fine; you may wish to specify a particular [node name][5] – this can be done using the RABBITMQ_NODENAME environment variable

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-00-52.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-00-52.png" alt="" /></a></figure>
</div>

That’s it. Click Apply, and Apply again on the Summary screen.

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-01-13.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-01-13.png" alt="" /></a></figure>
</div>

The RabbitMQ docker container will start, and if everything has gone to plan, it should stay running and not restart. To check out the logs, select the container from the Container tab and click the Details button.

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-03-05.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-03-05.png" alt="" /></a></figure>
</div>

From the details, click the Log tab. If startup has been successful, you will the “Server startup complete; 3 plugins started.” message as shown below. Otherwise, these logs should give a useful indication what has gone wrong.

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-04-02-1.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-04-02-1.png" alt="" /></a></figure>
</div>

The RabbitMQ mnesia folder will be initialized in the folder specified earlier as  a mapped volume.

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-05-05.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-05-05.png" alt="" /></a></figure>
</div>

The RabbitMQ Management portal will be accessible through a web browser at port 15672 on your NAS’s hostname or IP address. But if you try to login using the default guest/guest credentials you will likely be met with the “User can only log in via localhost” message shown below. That’s not an option from the Synology NAS, which doesn’t have any web browser installed.

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-06-24-1.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-06-24-1.png" alt="" /></a></figure>
</div>

There are a couple of solutions to this quandary. The rabbitmq.conf file created earlier could be edited to allow the guest user to connect from a remote host by setting the loopback_users configuration to none – [details here][6].

Alternatively, the rabbitmqctl utility can be used to add a new user with administrator rights, as shown in the screenshot below.

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-23-57.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-23-57.png" alt="" /></a></figure>
</div>

Having done this, it will be possible to login to the RabbitMQ management console from a remote machine using the newly-created credentials.

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-24-50.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-24-50.png" alt="" /></a></figure>
</div>

Boom! There we have it. RabbitMQ running in a Docker image, on a Synology NAS, with the management plugin accessible from the local network.

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-25-45.png"><img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/2020-01-13_21-25-45.png" alt="" /></a></figure>
</div>

 [1]: https://www.synology.com
 [2]: https://www.docker.com/
 [3]: https://www.rabbitmq.com/
 [4]: https://blogstouks01.z33.web.core.windows.net/2023/08/1_2020-01-13_20-57-55.png
 [5]: https://www.rabbitmq.com/cli.html#node-names
 [6]: https://www.rabbitmq.com/access-control.html#loopback-users