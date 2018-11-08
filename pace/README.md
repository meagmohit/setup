# PACE @GT : CheatSheet
------------------------------

## Logging In
-------------
*  `ssh <username>@<login-node>.pace.gatech.edu` e.g. ssh <username>@login-s.pace.gatech.edu
*  **With X Server Display:** `ssh -X <username>@login-s.pace.gatech.edu`
*  `ssh <username>@iw-dm-4.pace.gatech.edu` for fast connection to all storage server (prefer over headnodes for internal data transfer)

Note: use `xclock` to check if the display is working. Use `-Y` flag if `-X` flag does not work

## General Info
-------------
*  Uses Moab Systems
*  Effective Storage Use
    *  ``home(5G):`` Store irreplaceable data here
    *  ``data(200G):`` Store long-term data here
    *  ``scratch(7T):`` Store short-term data here (data that is generated during application execution)
*  `/usr/local/pacerepov1` Location of pace soft

## Commands
-------------

### Standard

*  `groups` : Groups or queues you are part of
*  `pace-whoami` : Gives information regarding queues, walltimes, priority and login-nodes
*  `pace-quota` : Provides PACE storage quota for the account
*  `pace-check-queue <queuename>` : To check running jobs on a pace queue e.g. `pace-check-queue force-gpu`

    
### Job-related

*  `qstat` : Check the running job status
    *  `qstat -u <username> -n` : Filters running jobs based on username
    *  `qstat <queue-name>` : Filters jobs based on queue name e.g. `qstat force-gpu`
*  `showq` : Query for specific jobs/queues
    *  `showq -w class=<QueueName>,user=<UserID>` : All jobs for the queue and user
    *  `showq -r -w user=<UserID>` : All running jobs for the given user
    *  `showq -b -w class=<UserID> ` : All blocked jobs for the given user
*  `checkjob -v <JobID>` : Descriptive information about the particular job
*  `qdel <JobID>` or `canceljob <JobID>` : To remove or cancel jobs if submitted using `qsub` and `msub` respectively

### Module-related

*  `module avail` : List of all available modules
*  `module list` : List of all loaded modules
*  `module load <modulename>` : To load a particular module
*  `module rm <modulename>` : To remove a particular module
*  `module help <modulename>` : To get help on a particular module

### Loading modules at login

*  `~/.pacemodules` edit file to include
```
module load abc/1.0.0
module load xyz/13.4.5
```

## Submitting Jobs
-------------

### Interactive Jobs

* `qsub -I -q <queue-name> -l nodes=<#cpu>:ppn=<#cores>:gpus=<#GPUs>:exclusive_process,walltime=<time>,pmem=<#gbmemory>`
    *  `qsub -I -q force-gpu -l nodes=2:ppn=4:gpus=1:exclusive_process,walltime=00:120:00:00`
    *  `qsub -I -q force-gpu -l nodes=2:ppn=4:gpus=1:exclusive_process,walltime=00:120:00:00`
    *  `qsub -I [-X for visual] -q nvidia-gpu -l nodes=nvidiagpu,walltime=15:00:00`
* `nvidia-smi` Gives GPU availability on compute node



### Batch Jobs
* save file as `<filenmae>.pbs` and run as `msub <filename.pbs>` or `qsub <filename.pbs>`
```
#PBS -N job1
#PBS -l nodes=2:ppn=4:nvidiagpu
#PBS -l pmem=2gb
#PBS -l walltime=15:00:00
#PBS -q force-gpu
#PBS -j oe
#PBS -o myjob.out
#PBS -m abe
#PBS -M youremail@gatech.edu

cd $PBS_O_WORKDIR

hostname
module load <module name>
python <scriptname>
```

    *  -N for <jobname>
    *  -j and -o for output and error files
    *  -m and -M for notifying through email for start, finish and error
    

## Contact for issues
-------------
Email: pace-support@oit.gatech.edu


## References
-------------

[1] [PACE Orientation Gatech](http://pace.gatech.edu/sites/default/files/pace_orientation_0.pdf)

[2] [PACE-ICE Orientation Gatech](http://pace.gatech.edu/sites/default/files/pace-ice_orientation_0.pdf)

[3] [Working with Anaconda on PACE](https://pace.gatech.edu/how-do-i-install-my-python-package)

[4] [Working with Anaconda on PACE](https://pace.gatech.edu/how-do-i-install-my-python-package)
