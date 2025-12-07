# IP-Troubleshooting
Internet Protocol Troubleshooting Commands
## AWS Bastion + Private Instance Lab

### IPs
- Bastion Instance: 10.0.1.43
- Private Instance: 10.0.2.4 (ID: i-054aab171decf9cd1)

### Connection Result
From Bastion, the following command was tested and succeeded:
```bash
ssh -i My-Keypair.pem ec2-user@10.0.2.4
### Connection Result
From Bastion, the following command was tested and succeeded:
```bash
ssh -i My-Keypair.pem ec2-user@10.0.2.4
## Troubleshooting Notes

### SSH to Private Instance via Bastion

**Issue:**  
Initial SSH attempt from Bastion to private instance (`10.0.2.4`) failed.

**Cause:**  
Missing inbound rule in the private instance's Security Group. SSH (port 22) was not allowed from Bastion's Security Group.

**Solution:**  
Added inbound rule to private instance's SG:  
- Type: SSH  
- Source: Bastion's Security Group (ID)

After applying the rule, SSH connection succeeded.

**Confirmation:**  
Logged in successfully using:  
```bash
ssh -i My-Keypair.pem ec2-user@10.0.2.4
