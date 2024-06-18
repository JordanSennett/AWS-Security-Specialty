# EC2 Key Pairs 

- Keep your private key secure (no way to recover it)
- You can create Key Pairs outside of AWS and upload them
- Both ED25519 and 2048-bit SSH-2 RSA keys are supported

<img width="545" alt="Screenshot 2024-06-17 at 7 10 32 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/2f95fb49-a222-4550-950f-f5cbaaafc274">


**EC2 Key Pairs – Notes**

- Key Pairs don’t get deleted from EC2 instance’s root volumes when the Key Pair removed from the EC2 Console
- Launching an EC2 instance with prebuilt AMI, the old Key Pair will exist alongside with the new Key Pair

<img width="297" alt="Screenshot 2024-06-17 at 7 11 30 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/5c1e1f30-1567-499e-8be8-98081427d78a">

**Remediating Exposed EC2 Key Pairs**

- Remove all the public keys in ~/.ssh/authorized_keys file on EC2 instances
- Create a new Key Pair and add its public key to the ~/.ssh/authorized_keys file on all EC2 instances
- Note: Use SSM Run Command to automate the process add/delete public keys on EC2 instances
  
<img width="658" alt="Screenshot 2024-06-17 at 7 17 41 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/70ec405f-7239-4a61-9ab2-792b5102385c">

**EC2 Instance Connect Browser Based SSH - Explanation**

<img width="657" alt="Screenshot 2024-06-17 at 7 18 29 PM" src="https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/62a96bbf-0490-4f85-a4f3-af6c6b5d359c">






