<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400"></a></p>

<p align="center" style="font-size: 32px;margin-left: 70px">
      Supervisor
</p>

## How to install Supervisor ?

#### Step1 : first updating system packages :

```phpregexp 
    sudo yum update -y 
```

##### Step2 : Install EPEL Repository:

```phpregexp
    sudo yum install epel-release
```

#### Step3 : Update and Install Supervisor:

```phpregexp
    sudo yum update
    sudo yum -y install supervisor
```

### Step4 : Then start and enable the supervisord daemon to start on boot using the commands below:

```phpregexp
    sudo systemctl start supervisor
    sudo systemctl enable supervisor
```

<p align="left" style="font-size: 16px;color: #be3f3f">
    Issue the command below to check the status of the service with the command below
</p>

```phpregexp
    sudo systemctl status supervisor
```

<p align="left" style="font-size: 16px;color: #be3f3f">
    for stop running supervisor run this command:
</p>

```phpregexp
    sudo systemctl stop supervisor
```



### Step5 : Go to ( /etc ) folder and find (supervisor.conf) file and past this config end of file:

```bash
    [program:laravel-worker]
    process_name=%(program_name)s_%(process_num)02d
    command=php *your artisan file address* *your command *
    autostart=true
    autorestart=true
    stopasgroup=false
    killasgroup=true
    user=f1app
    numprocs=1
    stopwaitsecs=3600
    startsecs=0
    
```

### Step6 : run this commands for reread and update  config file  after changes:

```phpregexp
    sudo supervisorctl reread

    sudo supervisorctl update
    
```

### End : start your program with this command :
 ```phpregexp
     sudo supervisorctl start laravel-worker:*
  ```

<p align="left" style="font-size: 16px;color: #be3f3f">
    check yore program status  :
</p>

```phpregexp
    sudo supervisorctl status laravel-worker:*
```





<p align="left" style="font-size: 16px;color: #be3f3f">
    stop your program :
</p>

```phpregexp
    sudo supervisorctl stop laravel-worker:*
```



<p align="center" style="font-size: 28px;color: #8828c1">
    vista developers
</p>
