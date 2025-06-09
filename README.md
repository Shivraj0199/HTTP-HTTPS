## Steps to host your website on a domain name with HTTPS (SSL) from scratch - using an EC2 Ubuntu instance + NGINX + Let's Encrypt SSL.
---

### **🎯 Goal:**

**Make your website accessible at:**

`✅ https://yourdomain.com`

`🔁 Automatically redirect http://yourdomain.com → https://yourdomain.com`

## **Step 1:  Point Domain to EC2 Public IP**

1) Go to your domain registrar (GoDaddy, Hostinger, etc.)
2) Find DNS settings or Manage DNS
3) Add an A Record:


      **`Host:       @`**

      **`Type:       A`**

      **`Value:      <Your EC2 Public IPv4 IP>`**

      **`TTL:        Default or 3600`**
   

4) Add another A record:


      **`Host:       www`**
  
      **`Type:       A`**
  
      **`Value:      <Your EC2 IP>`**


## **Step 1:  SSH into EC2**

`ssh -i your-key.pem ubuntu@<your-ec2-ip>`

## **Step 3: Install NGINX Web Server**

  `sudo apt update`

  `sudo apt install nginx -y`

#### Enable and start Nginx

  `sudo systemctl enable nginx`

   `sudo systemctl start nginx`

#### Test: Open in browser:

`http://yourdomain.com
`

## **Step 4: Upload Your Website Files (HTML or App)**

#### Replace Nginx default page
  
`cd /var/www/html`

`sudo rm index.nginx-debian.html`

`sudo nano index.html`

#### Paste your HTML code (e.g., Hello from My Domain!) → Save with CTRL+O, exit with CTRL+X

## **Step 5: Install Certbot for Free SSL (HTTPS)**

`sudo apt install certbot python3-certbot-nginx -y
`

## **Step 6: Generate SSL and Force HTTPS**

`sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com
`

## **Step 7: Test HTTPS and Redirect**

`https://yourdomain.com
`


   


