## Vagrant Docker

A little Vagrant file to manage and provison a VM with Docker for your projects.

### Requirements

* Vagrant
* Pizza & Beer

### Usage

* Run `vagrant up --provision`
* Add your project(s) to `sites/`
* Visit [http://192.168.50.4](http://192.168.50.4)
* And Enjoy :)

### Notes

* You could add 192.168.50.4 to your hosts for local DNS
* I recommend to explicity define the synced_folder on as your work project basis in the Vagrant file as the NFS may slow down otherwise.


### Contributors
Paul Stewart