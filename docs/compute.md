# How to run computational experiments?

This document describes the alternatives we have to run our experiments.

## Physical machines hosted in Assert

* Individual NUC
* repairnator: 130.237.222.185, 125GB RAM, two GPUs

```
Repairnator disks I/O profile
dd if=/dev/zero of=./tmp_output conv=fdatasync bs=384k count=1k; rm ./tmp_output

Fast IO
/mnt/nvme 1.2 GB/s
/mnt/ssd1 425 MB/s
/mnt/ssd2 425 MB/s
/mnt/ssd3 423 MB/s
/          340 MB/s
Slow IO
/mnt/hdd1 210 MB/s
/mnt/hdd2 229 MB/s

```

* pellow: 130.237.224.46, 46GB RAM, one GPU
* tiramisu: 130.237.224.95, 46GB RAM, one GPU

## Physical machines hosted at KTH

* croaker: croaker.eecs.kth.se, 130.237.72.200, 500GB RAM, 128 processors (AMD EPYC 7742 64-Core Processor, 1495 Mhz) 

* GPU NVIDIA DGX H100 at EECS <https://intra.kth.se/en/eecs/nyheter/resurs-for-larare-nvidia-dgx-h100-1.1314290>

For more machines, see <https://intra.kth.se/en/it/arbeta-pa-distans/unix/servers-1.971157>


## NAISS Cluster (formerly SNIC)

We have/had SNIC projects in four clusters, HPC2N, PDC, Alvis@C3SE, and Berzelius@NSC.
The last two are suited for GPU-intensive jobs.
They support Singularity/[Apptainer](https://github.com/apptainer/apptainer)

Open an account on https://supr.snic.se/, and ask to join an existing project on https://supr.snic.se/project/.

For Berzelius the PI is He Ye (search for her name). 
For the others the PI is Martin Monperrus.

Expert in the team for questions: Zimin, Javier Ron, Zhongxing

See documentation at the official documentation websites and at <https://github.com/gluckzhang/assert-gold-mine/blob/master/docs/snic-run-experiments.md>

## gpu1.eecs.kth.se

8 GPUs
https://gpu1.eecs.kth.se/

## KTH Cloud (run by students)

cbhcloud is top for master's students, has 15 GPUs
see https://cloud.cbh.kth.se/
ask for access on Discord

## WASP Cluster

We can have virtual machines in the WASP cluster operated by Ericsson. 
OpenShift interface

We self-operate(d) a Kubernetes cluster there. Can be used with [argo](https://github.com/argoproj/argo) (Javier has done this)


## Cloud

We can spawn VMs or any other cloud services on Azure. The costs are paid on a research grant. 

### Microsoft Azure

We have a Microsoft Azure account. Expert in the team for questions: Javier

To extract/recover data from a shutdown disk.

- Create a snapshot from the disk
- Create a snapshort export URL from the snapshot
- Download the snaphot on a machine `az storage blob download -f file.vhd --blob-url "<EXPORT_URL>"`
- Mount the file as loop `losetup -P /dev/loop100 file.vhd`
- Mount the file as filesystem `mount -t auto /dev/loop100p1 /mnt/disk`
- Copy the content `cp -a /mnt/disk /where/you/want`
  
### Google Cloud / GCP

We have a Google Cloud GCP account. 

Expert in the team for questions: Cesar, Zimin


## Not enough?

Just ask on the mailing-list :)
