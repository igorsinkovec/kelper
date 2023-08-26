# Kelper

Kelper is a [kelp bot](https://github.com/stellar/kelp) helper.


## What is it for

Running kelp bot manually has proven to be quite tedious for a few reasons, the biggest one for me was having to memorize and type out all the long commands. Kelper can run kelp commands in a very shorthand form.

## What it can do

Along with running most kelp commands, it can fetch the latest price from Horizon and write it to the strategy config file (only Pendulum currently supported). More features are under development.


This is the output of the help function:

```
kelper is a kelp bot helper.

---------------------------------------------------------------------------------
kelper expects its config file kelper.cfg to be present in the current directory.
If you intend to run multiple instances of kelper (like a kelp bot farm),
best practice is to create multiple directories containing the required
config files, one for each instance.

kelper depends on: kelp (obviously), curl, jq (to fetch and extract latest price).
These should be made available in your shell PATH.

---------------------------------------------------------------------------------

Usage: kelper [COMMAND]... [OPTION]...

Examples:
  kelper price -m 0.5 2
  kelper up -d -l
  kelper status

Commands:
  price     Update pendulum strategy config with latest trade price
  up      	Start kelp bot
  status  	Show kelp bot status
  stop    	Stop kelp bot
  down    	Stop kelp bot and delete all orders

Options:
  -m, 		When updating latest trade price for pendulum strategy, also set
      		    MIN_PRICE and MAX_PRICE limits. The argument values in the
      		    above example will set MIN_PRICE and MAX_PRICE limits to half
      		    and double the current price, respectively.
  -d, 		Run kelp in background
  -s, 		Run kelp in simulation mode
  -l, 		Write kelp standard output to a log file
  -v, 		Show version
  -h, 		Show this help info
```


## Get kelper

Download from this repository, copy to your PATH and make executable:

```
wget https://raw.githubusercontent.com/igorsinkovec/kelper/master/scripts/kelper
chmod +x kelper
sudo mv kelper /usr/local/bin
```

A sample kelper config file is available here: [kelper.cfg](https://github.com/igorsinkovec/kelper/blob/master/config/sample-kelper.cfg)

You will also need to provide the required dependencies for kelper to be able to run.
[**Kelp**](https://github.com/stellar/kelp) is the obvious one, **curl** is most likely already present
on your system, and you should be able to get [**jq**](https://stedolan.github.io/jq/) from official repos of your distro.
On Ubuntu 22 you can install jq from snap: `sudo snap install jq`.
