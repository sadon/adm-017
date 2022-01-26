1. Create and connect to baked VM:

Run `terraform apply` 

2. Execute next command `terraform show`

3. Extract ssh-key 

`terraform show -json | jq -r '.values.root_module.resources | map(select (.type | contains("tls_private_key"))) | .[].values.private_key_pem'  > ~/.ssh/tf-key`

4. `chmod 0600 ~/.ssh/tf-key`


5. Review external ip-address by 2 ways:
- Review in state 
- Programmatically:
`terraform show -json | jq -r '.values.root_module.resources | map(select (.type | contains("aws_instance"))) | .[].values.public_ip'`

ex: "18.198.50.221"

6. Connect to VM using exteran IP_address, ex.:
   `ssh -i ~/.ssh/tf-key ec2-user@18.198.50.221`
   

7. Destroy VM
   `terrafrom destroy`

---
Notes
- Create ~/.ssh folder if it didn't exist: `mkdir -p ~/.ssh`
- Use `-r` flag for jq to replace **\n** to  **RAW** newlines
- Setup correct permissions for keys `chmod 0600 ~/.ssh/tf-key`