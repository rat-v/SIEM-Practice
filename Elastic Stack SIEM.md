In this project, I set up an Elastic Stack SIEM in my home lab. I
practice generating events on a Kali VM, and get hands-on experience in
installing an agent to forward the data to the SIEM. I also get
experience in querying and analyzing the logs sent. I will also
visualize the security and events and learn how to generate security
alerts when a rule has been triggered.

There were some initial steps I took that don't really need
documentation: creating an Elastic Account and booting up my Kali VM.
Now, I want to push telemetry from my Kali VM to the SIEM using an
agent.

### Setting up the SIEM to collect logs 

I install an integration called "Elastic Defend" and paste the
installation command onto my Kali's terminal

![](output\Elastic Stack SIEM/media/image10.png){width="7.369792213473316in"
height="5.125784120734908in"}

![](output\Elastic Stack SIEM/media/image21.png){width="8.536458880139982in"
height="3.02332895888014in"}

After some time, it installs successfully. I can also run a command,
**sudo systemctl status elastic-agent.service** , just to verify
everything is running
normally.![](output\Elastic Stack SIEM/media/image13.png){width="8.994792213473316in"
height="3.063850612423447in"}

![](output\Elastic Stack SIEM/media/image5.png){width="8.702199256342958in"
height="2.432292213473316in"}

### Generating Security Events

#### Nmap

Now is the time to test this out. I can run some security related
commands like running Nmap to create some events that the SIEM should
pick up. I run some simple scans, then some more aggressive ones.

![](output\Elastic Stack SIEM/media/image12.png){width="5.109375546806649in"
height="3.852214566929134in"}

![](output\Elastic Stack SIEM/media/image24.png){width="6.755208880139983in"
height="5.347872922134733in"}

#### SSH

I can also try and start an SSH session with other server to generate
some logs

![](output\Elastic Stack SIEM/media/image15.png){width="8.9375in"
height="2.3541666666666665in"}

![](output\Elastic Stack SIEM/media/image9.png){width="7.182292213473316in"
height="4.945307305336833in"}

### Querying for Security Events in the SIEM

Moving into the logs section of the SIEM, I can already see some
telemetry generated

![](output\Elastic Stack SIEM/media/image25.png){width="4.635416666666667in"
height="3.3541666666666665in"}

#### Nmap

Now I can query for **process.args:"nmap"** and see events that
correlate to the scans I conducted

![](output\Elastic Stack SIEM/media/image6.png){width="5.213542213473316in"
height="3.858559711286089in"}

![](output\Elastic Stack SIEM/media/image16.png){width="10.0in"
height="2.8055555555555554in"}

![](output\Elastic Stack SIEM/media/image22.png){width="10.0in"
height="2.5694444444444446in"}

#### SSH

I can also see the SSH sessions I tried to start. Very useful to see
attempted SSH logins that were either blocked or refused from an
incorrect password

![](output\Elastic Stack SIEM/media/image11.png){width="10.0in"
height="2.7916666666666665in"}

![](output\Elastic Stack SIEM/media/image23.png){width="10.0in"
height="2.8194444444444446in"}

### Visualization

A dashboard can be created to visualize these events, making it much
easier to go through all these logs.

![](output\Elastic Stack SIEM/media/image14.png){width="7.307292213473316in"
height="4.223480971128609in"}

I choose to visualize it with vertical bars, setting the axes to be
Count of records vs Time

![](output\Elastic Stack SIEM/media/image8.png){width="10.0in"
height="3.625in"}

The time frame is too small, so I can change the settings to expand it.
I also can mess around with different visualization methods..

![](output\Elastic Stack SIEM/media/image20.png){width="4.613774059492563in"
height="5.816060804899387in"}

![](output\Elastic Stack SIEM/media/image2.png){width="6.713542213473316in"
height="3.300824584426947in"}

![](output\Elastic Stack SIEM/media/image7.png){width="6.630208880139983in"
height="3.2792268153980753in"}

### Creating an Alert

I will create an alert that will be triggered upon an Nmap scan to
notify me when it is detected. This rule will run every 5 minutes and
will send me an email when it's triggered by an Nmap scan.

![](output\Elastic Stack SIEM/media/image4.png){width="8.03125in"
height="1.5208333333333333in"}

![](output\Elastic Stack SIEM/media/image18.png){width="7.34375in"
height="3.40625in"}

![](output\Elastic Stack SIEM/media/image1.png){width="10.0in"
height="5.013888888888889in"}

![](output\Elastic Stack SIEM/media/image19.png){width="10.0in"
height="4.958333333333333in"}

Additional Nmap scans are conducted to trigger the rule and test if the
alert works.

![](output\Elastic Stack SIEM/media/image17.png){width="6.609375546806649in"
height="4.982310804899387in"}

And I get the email notifying me of the alert.

![](output\Elastic Stack SIEM/media/image3.png){width="7.125in"
height="4.260416666666667in"}

Overall, this was a beneficial lab. I set up an Elastic SIEM and a Kali
VM, and had it so the VM would forward data to the SIEM using an Elastic
agent. I generated security events by running Nmap and SSH, and queried
those logs in the SIEM. I created a dashboard to visualize security
events and then set up an email alert system.

Some future steps I can take is to practice working with the
visualization tools so I can be more efficient and effective in
understanding the logs.
