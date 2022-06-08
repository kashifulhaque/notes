# Automating Scripts

Date: March 14, 2022
Lecture #: 5
Lecture URL: https://youtu.be/kWid87j6qIE
Notion URL: https://21f1003586.notion.site/Automating-Scripts-e44cc42c2e594a1aa2b77d6c176175e5
Type: 📒 Lecture
Week #: 8

### `cron`

- Service to run scripts automatically at scheduled times
- Tools:
    - `at`
    - `crontab`
    - `anacron`
    - `logrotate`
- Script locations:
    - `/etc/crontab`
    - `/etc/cron.d`
    - `/etc/cron.hourly`
    - `/etc/cron.daily`
    - `/etc/cron.weekly`
    - `/etc/cron.monthly`

### Job definition

![Untitled](Automating%20Scripts%20d5f259340602471482d4ec24227ba72a/Untitled.png)

### Startup scripts

- `/etc/init/`
- `/etc/init.d/`

Runlevel scripts

![Untitled](Automating%20Scripts%20d5f259340602471482d4ec24227ba72a/Untitled%201.png)

### To create a `cron` job

`crontab -e`

Add your cron job at the end of the file

![Untitled](Automating%20Scripts%20d5f259340602471482d4ec24227ba72a/Untitled%202.png)

It should execute as per your mentioned cron timings

System-wide crontab

![Untitled](Automating%20Scripts%20d5f259340602471482d4ec24227ba72a/Untitled%203.png)