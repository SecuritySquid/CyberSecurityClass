## Activity File: Interview Questions

- This first project covers a wide range of topics including cloud, network security, and logging and monitoring.

- When networking and talking to potential employers, you should be able to reference the work done on this project to answer specific interview questions or demonstrate your skills within a specific domain. 

- You will choose a domain that you're interested in pursuing as a career and answer mock questions based on the suggested response format. 
​
### Instructions 

1. Choose one of the following domains:
    - Network security
    - Cloud security
    - Logging and monitoring

    If you are unsure of which domain you want to focus on, that's okay. You can either choose the one you're most comfortable discussing, or complete the tasks in two or all three domains.

2. Select one domain and one question. 

    - Questions are provided for each domain. Choose one to answer from your chosen domain. 
​
3. Write a one-page response that answers the question using specific examples from your work on Project 1. Your response should flow and read like a presentation while keeping the general structure of the technical question response guidelines. 

    You will submit this one-page response. 

#### Reminder: Response Guidelines
As a reminder,  good responses do the following. 
​
1. Restate the problem.
2. Provide a concrete example scenario.
3. Explain the solution requirements.
4. Explain the solution details.
5. Identify advantages and disadvantages of the solution​.
​
Including each of these components will ensure you prove your competency of subject matter and critical thinking. 
​
### Interview Questions by Domain

Below you will find a list of questions, grouped by specific domains. Select one question to answer. 
​ 

For each question, where appropriate, we have provided you with specific prompts to consider as you structure each section of your response. Feel free to use these prompts or your own examples. 

#### Domain: Network Security

**Question 1:  Faulty Firewall**

Suppose you have a firewall that's supposed to block SSH connections, but instead lets them through. How would you debug it?

Make sure each section of your response answers the questions laid out below.
​
1. Restate the Problem
    The issue of unwanted connections gettting through a supposed firewall setting can be caused by a few things. 

2. Provide a Concrete Example Scenario
    - In Project 1, did you allow SSH traffic to all of the VMs on your network?
        For example in the first project, we needed some adminastrative access to the vms on the network but we didn't want those vms accessable to a public ssh connection.
    - Which VMs did accept SSH connections?
        To mitigate this we used security settings to allow local ssh connection to internal machines and used a gateway machine that can reach machines on the local network.
    - What happens if you try to connect to a VM that does not accept SSH connections? Why?
        This way if someone tries to connect to the VM directly the network will refuse the connection.

3. Explain the Solution Requirements
    - If one of your Project 1 VMs accepted SSH connections, what would you assume the source of the error is?
        If the machine had an issue like this I would first check firewall config
    - Which general configurations would you double-check?
        Things like the syntax of the ssh rule, correct ports, correct priority
    - What actions would you take to test that your new configurations are effective?
        Attempt to violate the rule in a direct connection.


4. Explain the Solution Details
    - Which specific panes in the Azure UI would you look at to investigate the problem?
        Things like checking the Network Security Group, check the inbound and outbound rules
    - Which specific configurations and controls would you check?
        Make sure the machines are using the correct controls like using the correct nsg, part of the correct vnet, ect.
    - What would you look for, specifically?
        Am I on the right network, does the rule look right, is it at a high enough priority, did I set up the right region for all these resources. Are the IP addresses used the correct values.
    - How would you attempt to connect to your VMs to test that your fix is effective?
        Most likely a direct public ssh connnection.

5. Identify Advantages/Disadvantages of the Solution

    - Does your solution guarantee that the Project 1 network is now "immune" to all unauthorized access?
            If the gateway machine or some other machine is compromised then it could be possible to ssh within the local netowrk but that too could be further mitigated with additional network segrigation. 

    - What monitoring controls might you add to ensure that you identify any suspicious authentication attempts?​
        Using the elk server to monitor the internal machines and gateway machines for suspicious internal network activity or changes to any serious system logs. 

**Question 2: Unsecured Web Server**

Suppose you find a server running HTTP on port 80, despite compliance guidelines requiring encryption in motion. What do you do?
​​
1. Restate the Problem
    The issue is that if a server is running HTTP when there is a compliance reason to require encryption it creates a serious security issue for the data sent/recieved on those servers. 
2. Provide a Concrete Example Scenario
    - In Project 1, did you have servers running HTTP on port `80`?  If so, why was it permissible to do so?
        Yes, we did use servers on port 80 but there were no concerns for keeping any data that need over the wire encryption.
    - In a real deployment, which specific machine would you configure differently? How, and why?
        In a real situation it is possible to have a server that hosts data over port 80 but it needs to be isolated in the network and there needs to be additional controls on the machine as far as what it can do, see, and run. 
3. Explain the Solution Requirements
    - Why is running HTTP on port `80` a potential problem?
        Any data sent or recieved over that server will be unencrypted.
    - How would you reconfigure a server to serve HTTP traffic safely?
        It would be better to force HTTPS in the header and by closing port 80 on the server in question.
    - How does this solution fix the problem?
        This will end any server from running on port 80.
4. Explain the Solution Details
    - Which tools and technologies would you use to implement this solution in Project 1?
        Using NSG inbound/outbound rules to deny connections over port 80.
    -  How, specifically, would you use these tools to harden your deployment?
        Using the new rules you can apply them to the machines you want to harden.

5. Identify Advantages and Disadvantages of the Solution
    -  Will your solution break clients that used to communicate with the server over port `80`?
        Yes it will completely prevent any connection. It is possible to create a legacy machine they can connect on port 80 to and then keeping that machine isolated on the internal network. 
    -  Do you have to do any work to keep this solution running longterm? Or can you simply "set it and forget it?”
        Depending on if you decide to maintain a legacy machine that would take extra monitoring and controls long term otherwise if you simply refuse connections just requires setting up some alerts in case anything changes. 


© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.  
