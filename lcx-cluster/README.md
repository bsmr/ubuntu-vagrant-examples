# Vagrant LXC Ubuntu cluster

## Setup

Install LXC on Ubuntu 14.04:

```bash
> sudo apt-get install lxc
```

Install the lxc provider for vagrant:

```bash
> vagrant plugin install vagrant-lxc
```

## Example configuration

Add a Vagrantfile with this content:
```ruby
Vagrant.configure("2") do |config|
  # Number of nodes to provision
  nodeCount = 4

  # Ubuntu 14.04 with LXC support
  config.vm.box = "fgrehm/trusty64-lxc"

  # Setup the nodes
  1.upto(nodeCount) do |num|
    # generate node name
    nodeName = ("node-%02x" % (num - 1)).to_sym
    # specify _settings_ for each node
    config.vm.define nodeName do |node|
      # TBD: example with proper values
    end
  end
end
```

## Power on the cluster

### _All_ the machines

```bash
> vagrant up --provider=lxc
```

### A _single_ node

```bash
> vagrant up --provider=lxc node-01
```

## Check the status

```bash
> vagrant status
```

