## Objective 

In this project, I set up an Elastic Stack SIEM in my home lab. I
practice generating events on a Kali VM, and get hands-on experience in
installing an agent to forward the data to the SIEM. I also get
experience in querying and analyzing the logs sent. I will also
visualize the security and events and learn how to generate security
alerts when a rule has been triggered.

## Skills Learned
Setting up a SIEM in a home lab environment<br>
Installing and configuring an agent to forward telemetry data to the SIEM<br>
Generating security events to test the SIEM setup<br>
Querying and analyzing logs to identify security events<br>
Visualizing the events to represent security data effectively<br>
Setting up alerting mechanisms to trigger notifications based on specific security events<br>


There were some initial steps I took that don't really need
documentation: creating an Elastic Account and booting up my Kali VM.
Now, I want to push telemetry from my Kali VM to the SIEM using an
agent.

## Setting up the SIEM to collect logs 

I install an integration called "Elastic Defend" and paste the
installation command onto my Kali's terminal

![image10](https://github.com/user-attachments/assets/2fffd6f6-1611-48e4-9860-26bc5f28089d)


![image21](https://github.com/user-attachments/assets/bf6152c0-b65a-4a1d-a4cb-72f4c10ae5a3)


After some time, it installs successfully. I can also run a command,
**sudo systemctl status elastic-agent.service** , just to verify
everything is running
normally.

![image13](https://github.com/user-attachments/assets/2eefc276-1d3e-46cb-9ca0-e5ebea646af7)


![image5](https://github.com/user-attachments/assets/00f1ddb3-34a0-4577-968d-ae871b014cf7)


## Generating Security Events

### Nmap

Now is the time to test this out. I can run some security related
commands like running Nmap to create some events that the SIEM should
pick up. I run some simple scans, then some more aggressive ones.

![image12](https://github.com/user-attachments/assets/f9cac93b-707a-4f11-b633-d4d1c14e3693)

![image24](https://github.com/user-attachments/assets/addfdccf-befc-4129-ba14-57ef6d9a8574)


### SSH

I can also try and start an SSH session with other server to generate
some logs

![image15](https://github.com/user-attachments/assets/5e670f1d-9e5b-4b8f-afb3-39cd6c4d0235)


![image9](https://github.com/user-attachments/assets/7fa3729f-46bb-455d-b011-caca986f25ed)


## Querying for Security Events in the SIEM

Moving into the logs section of the SIEM, I can already see some
telemetry generated

![image25](https://github.com/user-attachments/assets/399b6984-ad62-4f4d-989e-72e81012a513)


### Nmap

Now I can query for **process.args:"nmap"** and see events that
correlate to the scans I conducted

![image6](https://github.com/user-attachments/assets/7ab861f4-a877-43f3-b696-87c282778084)


![image16](https://github.com/user-attachments/assets/07d56e5a-b386-4a30-aef0-21c371aaaaf3)


![image22](https://github.com/user-attachments/assets/0018ed05-10fa-42ba-9605-92c1bcf7327d)


### SSH

I can also see the SSH sessions I tried to start. Very useful to see
attempted SSH logins that were either blocked or refused from an
incorrect password

![image11](https://github.com/user-attachments/assets/71436ba1-c3c8-4d8a-9b92-f7ea69d2994a)


![image23](https://github.com/user-attachments/assets/1baaf511-7860-4c99-9aff-03e8dd39c715)


## Visualization

A dashboard can be created to visualize these events, making it much
easier to go through all these logs.
![image14](https://github.com/user-attachments/assets/0a9487bc-5fe1-4749-b688-2282932acda8)


I choose to visualize it with vertical bars, setting the axes to be
Count of records vs Time

![image8](https://github.com/user-attachments/assets/7124fd6d-1dc5-40f2-9219-780c9421237c)


The time frame is too small, so I can change the settings to expand it.
I also can mess around with different visualization methods..

![image20](https://github.com/user-attachments/assets/a306384f-a7a9-4fc8-bd5d-94a42f8e258b)


![image2](https://github.com/user-attachments/assets/08526c4d-621a-4922-979c-ff17a2022624)


![image7](https://github.com/user-attachments/assets/20030c56-072a-4c07-8bf0-4cd563b31a48)


## Creating an Alert

I will create an alert that will be triggered upon an Nmap scan to
notify me when it is detected. This rule will run every 5 minutes and
will send me an email when it's triggered by an Nmap scan.

![image4](https://github.com/user-attachments/assets/64ee57c3-682c-49ca-a699-4ffa083f931b)


![image18](https://github.com/user-attachments/assets/30cb86c2-1845-4c03-ab61-32568357b55c)


![image1](https://github.com/user-attachments/assets/01308f2a-fde9-4d1d-9144-f25d50831b97)


![image19](https://github.com/user-attachments/assets/a21aa6b6-bfa3-4ff5-bc53-b0ceeae7b3aa)


Additional Nmap scans are conducted to trigger the rule and test if the
alert works.

![image17](https://github.com/user-attachments/assets/cb0d21d7-7b5b-47d0-8da1-3dd32545bdd5)


And I get the email notifying me of the alert.

![image3](https://github.com/user-attachments/assets/d05e6231-4415-4523-b7bb-3106ef49a53c)


Overall, this was a beneficial lab. I set up an Elastic SIEM and a Kali
VM, and had it so the VM would forward data to the SIEM using an Elastic
agent. I generated security events by running Nmap and SSH, and queried
those logs in the SIEM. I created a dashboard to visualize security
events and then set up an email alert system.

Some future steps I can take is to practice working with the
visualization tools so I can be more efficient and effective in
understanding the logs.
