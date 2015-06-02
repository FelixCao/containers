# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Start with a CentOS 7.1 box
  config.vm.box = "chef/centos-7.1"
  
  # Avoid problems with Booz Allen Web Gateway
  config.vm.box_download_insecure = true

  # Configure Virtual Box VM
  #
  config.vm.provider "virtualbox" do |vb|
     vb.memory = "5125"
	 vb.name = "docker_host"
  end


  # Update, install Docker, and trust the Booz Allen Web Gateway CA
   config.vm.provision "shell", inline: <<-SHELL
     sudo yum update -y
     sudo yum install -y docker
	 sudo cat > /etc/pki/ca-trust/source/anchors/ca.crt << EOF
-----BEGIN CERTIFICATE-----
MIIDyzCCArOgAwIBAgIBATANBgkqhkiG9w0BAQUFADBrMRwwGgYDVQQKDBNCb296
IEFsbGVuIEhhbWlsdG9uMQwwCgYDVQQLDANCQUgxEDAOBgNVBAcMB0FzaGJ1cm4x
CzAJBgNVBAgMAlZBMQswCQYDVQQGEwJVUzERMA8GA1UEAwwIYXNoYm1jd2cwHhcN
MTMwMTI5MTYwNjMzWhcNMjMwMTI5MTYwNjMzWjBrMRwwGgYDVQQKDBNCb296IEFs
bGVuIEhhbWlsdG9uMQwwCgYDVQQLDANCQUgxEDAOBgNVBAcMB0FzaGJ1cm4xCzAJ
BgNVBAgMAlZBMQswCQYDVQQGEwJVUzERMA8GA1UEAwwIYXNoYm1jd2cwggEiMA0G
CSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCfGLT5CyeBYNJdR/4UbFhnf05lCyjh
KVGrNKAAVwmbwEeKLPdhoghmdUgowsUpN4qcUNWtKPY6wAagZyw3SvW8rIAFbzxq
YsYSGdbCDzpkxZjyOKlXrbBSkaLekcsgvTj9FgbCmZ8kO0Tc/uE53QhIpEkT0gu1
LTLD5HEa5B2tJNufgtOhQesq4wONF/hhS+9itnVnkZLnqQwE7bcy/H426VDBIXWd
o8pPlaEzVtCbN8NUHXUvC/XmfCiB0i/zI9F8KBGXFPumSRVej66DdRv/6cBZN+Q4
5A486hkDxudYJrrcpingZnQLobrmEoC7E3nu/edjTWz+l5tAE/5o043TAgMBAAGj
ejB4MCoGCWCGSAGG+EIBDQQdDBtjZXJ0IGZvciBNY0FmZWUgV2ViIEdhdGV3YXkw
LwYDVR0RBCgwJoEkR09fQ3liZXJfU2VjdXJpdHlfT3BlcmF0aW9uc0BiYWguY29t
MAwGA1UdEwQFMAMBAf8wCwYDVR0PBAQDAgEGMA0GCSqGSIb3DQEBBQUAA4IBAQBV
EZezNi3k5yxj9hfVQyvJAyFJQGPzhOcIVXIB/GjfUd5H2OALrVWoSYTs8U2i0EX7
VPZ9f5ma77xqTDxI7wnV5eqXa4JVr4cFYcFlNFNLqm9itchcdPSNVR0cLNOn0l5M
fDf6bu25yRcK2pGCRd6DsadA7p6NTkKZ1vz6w7BTx5UPaZk5yDG/HBXdfyccxPQZ
/Q3/qouy19c7TCKlhX+siO4ON76hxl4BcWtEiyp5rb/AhkrjGrodiYoBzRqmQecJ
pCrl+1DLRatvOeWDMLxTqT0Mkb1PiK550gBINUz8hPPL4bTH9YVhs5f4EwYzhRFO
69YGt6dt3XehCp4wnzQ2
-----END CERTIFICATE-----
EOF
	 sudo update-ca-trust
	 sudo systemctl enable docker
	 sudo systemctl start docker
   SHELL
end
