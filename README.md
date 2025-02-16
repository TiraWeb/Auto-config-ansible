
## Setup Instructions

1. **Launch an AWS EC2 Instance:**
   - Log in to the AWS Management Console
   - Launch an Ubuntu t2.micro instance
   - Configure the security group to allow:
     - SSH (port 22) from your IP
     - HTTP (port 80) if you plan to view the nginx web server
   - Create a key pair and download the `.pem` file

2. **Configure the Inventory File:**
   - Edit `hosts.ini` with your EC2 instance details:
     ```ini
     [web]
     aws_webserver ansible_host=171.1.1.1 ansible_user=ubuntu ansible_ssh_private_key_file=key.pem
     ```
   - Replace the values with your instance’s IP and the path to your `.pem` file

3. **Run the Ansible Playbook:**
   - Open your terminal, navigate to the project directory, and run:
     ```bash
     ansible-playbook -i hosts.ini site.yml
     ```

4. **Verify the Deployment:**
   - open your web browser and navigate to the EC2 instance’s public IP. You should see the default Nginx welcome page.

## CI/CD Integration

This project integrates GitHub Actions to automate linting and syntax checks:

- **Workflow File:** `.github/workflows/ci.yml` contains steps to:
  - Check out the repository
  - Set up Python and install Ansible & ansible-lint
  - Run ansible-lint and a syntax check on the playbook
  

## Screenshots

1. **AWS EC2 Console**
   ![image](https://github.com/user-attachments/assets/aa1e118b-9483-4642-918a-bc124c6d2480)


2. **Terminal Output**
   ![image](https://github.com/user-attachments/assets/8d4dbb76-5d86-4eea-a9a3-ac50197048be)

   
3. **Nginx Web Page**
   ![image](https://github.com/user-attachments/assets/ba6b1cbc-8955-4b47-85bc-fd90a468a387)


4. **GitHub Actions Workflow**
   ![image](https://github.com/user-attachments/assets/12a38a4b-7e94-43e5-8ef3-7bdb5984c0dd)
   
(first run failed because of too many blanks in site.yml and main.yml)

  
6. **Project Structure:**
   ![image](https://github.com/user-attachments/assets/25ca9c63-22d8-4be0-b613-5f51e2b233ac)

