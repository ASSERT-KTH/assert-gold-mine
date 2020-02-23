# Run Experiments with SNIC

SNIC (Swedish National Infrastructure for Computing) is a Swedish research infrastructure, that makes available resources (data storage and computation) to meet the needs of researchers.

This document describes how to use HPC2N (High Performance Computing Center North), that is part of SNIC, in order to run the experiments in parallel.

## Requirements

### SUPR Account

To use the resources provided by SNIC, it is necessary to create a SUPR (SNIC User and Project Repository) account and join an existing project, as indicated in this [page](https://github.com/gluckzhang/assert-gold-mine/wiki/What-options-to-run-computational-experiments%3F).

If you have a KTH account, you can use the KTH credentials, otherwise you can create an account from [this page](https://supr.snic.se/person/register/new/?), and follow the instructions to accept the SNIC User Agreement.

More details can be found [here](https://www.hpc2n.umu.se/account/users).

### HPC2N Account

After becoming a member of an existing project, it is necessary to request an account at HPC2N in this [page](https://supr.snic.se/account/). More information are available in the point 4 of [this guide](https://www.hpc2n.umu.se/account/users).

## Login

After completing the steps of the Requirements section, you can access HPC2N clusters, using your HPC2N login name and password.

Based on the name of the resource associated with the project ('Abisko' or 'Kebnekaise'), you have to open an SSH connection in this way:

```
for Abisko: ssh yourusername@abisko.hpc2n.umu.se
for Kebnekaise: ssh yourusername@kebnekaise.hpc2n.umu.se
```

The first time, you will have to change the password, following [this guide](https://www.hpc2n.umu.se/documentation/access-and-accounts/login-password#first-login).

## Configuration of the Environment

### Load the necessary packages

To set up your environment for using a particular set of software packages, you can use the modules that are provided centrally.

To know the modules that are available, you can run this command:

```
 ml spider <software-name>
 ```

For instance, if you are interested to know which versions of Java are available, the command is this one:

```
ml spider Java
```

and the output will be similar to this one:

```
  Java:

    Description:
      Java Platform, Standard Edition (Java SE) lets you develop and deploy Java applications on desktops and servers. 

     Versions:
        Java/1.8.0_121
        Java/1.8.0_144
        Java/1.8.0_152
        Java/1.8.0_162
        Java/1.8.0_172
        Java/1.8.0_181
        Java/1.8.0_202
        Java/11.0.2
```

Thus, if you want to load `Java 1.8.0_202`, you have to run this command:

```
ml load Java/1.8.0_202
```

More details can be found in [this page](https://www.hpc2n.umu.se/documentation/environment/lmod).

`Every time you do the login, you have to reload the modules that you want.`

To ease the process, you can create a .sh file, where you put all the modules that have to be loaded, and source directy that file every time you do the login.

Example of the file:

```sh
#!/bin/bash
ml load Java/1.8.0_202
ml load Maven/3.6.0
```

To see the list of the loaded modules, you can run the command `ml`.

### Save personal information

If you need to save personal information, such as your GitHub OAuth token, you can save it in the `Private` folder, that is located in your `home`.

Indeed, all the other folders are public, and so they are accessible by everyone.

## File System and User Quota Limits

After setting your environment, you can start to create the jobs to run your experiments in parallel.

It's important to understand that there are two different file systems (`AFS` and `PFS`): your home is placed on the AFS file sysyem (it is backed up regularly), while the `pfs` folder (not backed up) used to run the experiments in parallel is in the PFS file system.

To create a soft link from your home directory to your corresponding home on the parallel file system, you can use the following command:

```
ln -s /pfs/nobackup$HOME $HOME/pfs
```

In this way, your "parallel" home directory will be available here `~/pfs`.

Every user has a maximum quota related to the space and to the number of the files that can be stored in the PFS file system. If your experiments exceed the quota, you will get the error `Disk quota exceeded`.

To check your quota limits, you can use the command: `quota`.

If your experiments creates many temporary files, you can save these files in the `/scratch` folder (if it is available) to try to avoid the quota exceeding.

More details are available in [this page](https://www.hpc2n.umu.se/documentation/filesystems/overview=).

## Creation of the Jobs

To run your experiments in parallel, you need to create a job for every experiment. Thus, you have to create a .sh file that follows this structure:

```sh
#!/bin/bash
#SBATCH -A <account>
#SBATCH -n <number-of-noded>
#SBATCH --time=01:00:00

srun ./mpi_program 
```

`#SBATCH -A` specifies the project ID of which you are a member. You can find the project ID in [this page](https://supr.snic.se/project/);

`#SBATCH -n` specifies the number of nodes that you want to allocate for the job;

`#SBATCH --time` specifies the time that should be reserved for the job (in the example, it has been specified one hour).

`srun` contains the command that have to be executed by the job (generally, you should run your parallel program with `mpirun` on `Kebnekaise` and `srun` on `Abisko`).

For instance, if you want to run [Repairnator](https://github.com/eclipse/repairnator) on the build `346537408` and reserve three hours to its job, you can create a file with this content:

```sh
#!/bin/bash
#SBATCH -A <project-id>
#SBATCH --time=03:00:00

srun java -cp $TOOLS_JAR:repairnator-pipeline-3.3-SNAPSHOT-jar-with-dependencies.jar fr.inria.spirals.repairnator.pipeline.Launcher --ghOauth $GITHUB_TOKEN --workspace /scratch/<username>/workspace --repairTools AstorJKali -b 346537408`
```

Moreover, it is possible to specify other parameters, following the indications of [this page](https://www.hpc2n.umu.se/quickstart).

## Run the Jobs

To run the jobs, you have to run this command:

```
sbatch <submit_file>
```

where `submit_file` is the name of the .sh file associated with the job. When the job is submitted, an ID is associated to this job.

For every job, it will be created a file `slurm-jobid.out` with the standard output and standard error.

To see the queue of your submitted jobs and their ID, you have to use this command:

```
squeue -u <username>
```

To cancel a job, you can use this command:

```
scancel -u <jobid>
```

To cancel all your jobs (running and pending) you can run this command:

```
scancel -u <username>
```

More information can be found [here](https://www.hpc2n.umu.se/batchsystem).

If you have many jobs to run, to ease the process of submitting all the jobs, you can create a .sh file in which you put the names of all your jobs and then you can source directly that file.

Example of the file:

```sh
#!/bin/bash

sbatch job-1.sh
sbatch job-2.sh
```