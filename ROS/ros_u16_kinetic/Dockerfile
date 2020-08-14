FROM osrf/ros:kinetic-desktop-full

# Set apt mirror to ucmirror and install extra packages
RUN sed -i "s/http:\/\/archive.ubuntu.com/http:\/\/ucmirror.canterbury.ac.nz/g" /etc/apt/sources.list && \
	apt-get update && \
	apt-get install -y \
		bash-completion \
		nano \
		tmux \
		ipython \
		ros-kinetic-rosbash \
		psmisc \
		python-scipy && \
	rm -rf /var/lib/apt/lists/*

# Sourcing this before .bashrc runs breaks ROS completions
RUN echo "\nsource /opt/ros/kinetic/setup.bash" >> /root/.bashrc




#RUN groupadd sshgroup && useradd -ms /bin/bash -g sshgroup sshuser
#RUN echo 'root:132' | chpasswd


#CMD service ssh start

# configure an SSH server in case we want to debug something
RUN apt-get update && apt-get install -y openssh-server
RUN ssh-keygen -A
ADD ./sshd_config /etc/ssh/sshd_config
RUN echo root:132 | chpasswd
RUN service ssh start