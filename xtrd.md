# XTR-Daemon


writer: huang@irl-recording.com

date: 2017-4-13



## Introduction

IPTap-Giga is a different project with old IPTap. It's run a linux os and support Gigabit network. 

You can reference other documents. <https://iprec.github.io/sipRecorder/ipRec-Giga-base>

XTR-Daemon is a Daemon process will running in IPTap-Giga. It commincate with XTR-software.

* running in IPTap-Giga.
* get network data via libpcap
* communcate with XTR-software via network interface.
* filter funciton via get XTR-software's config
* send IPPhone data to XTR-sofwarwe.


## connect to XTR-software

We can use network interface let IPTap-Giga connect to XTR-sfotware. the following chart explains how they communicate. 

```
                 IPTap-giga                 PC
                (xtr-daemon)            (xtr-client)
                     |                      |
                     | <--UDP broadcast---- | 1.Who's ipRec
           I'm ipRec | ---UDP socket------> |
                     | <--TCP connect ask-- | 2.connect ipRec
          connect ok | ---connect ok------> |
                     | <------------------- | 3.config ipRec
           config ok | -------------------> |
                     | <------------------- | 4.start data recevie
          receive ok | -------------------> |
                     |                      |
                     | -------------------> | 
                     |                      |
        network data | -------------------> | 5.recevie network data
                     |                      |
                     | -------------------> |
                     |                      |
                     | <------------------- | 6.stop data recevie
             stop ok | -------------------> |
                     | <------------------- | 7.close
            close ok | -------------------> |
                     |                      |

```

## how to do

1. use standard c/c++ to write XTR-daemo's code.
2. write&test XTR-daemon on Windows OS.
3. transplant XTR-daemon to IPTap-Giga.




