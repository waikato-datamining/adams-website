.. title: ADAMS and Docker
.. slug: adams-and-docker
.. date: 2020-03-04 16:41:57 UTC+13:00
.. tags: docker
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

For a while now, I've been working on getting ADAMS running on Docker,
with some of the snapshots now being deployed weekly to the public
`Docker hub <https://hub.docker.com/u/theadamsflow>`__. However, 
these images may not be suitable (or simply too large) and I therefore 
launched another little tool today called
`adamsflow2docker <https://github.com/waikato-datamining/adamsflow2docker>`__. 
This tool streamlines the process of deploying a worker flow (e.g., 
for processing data) within a Docker image.

Links to the *adamsflow2docker* tool and more detailed instructions on
running ADAMS from within Docker are available from `here <link://slug/docker>`_.
