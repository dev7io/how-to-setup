Setting up a web server using Nginx involves several steps, including installation, configuration, and testing. Here's a basic guide to help you set up a simple web server using Nginx on a Linux system. These instructions assume you have sudo or root access on your server.

### Step 1: Update the Package Repository

Update the package repository to ensure you have the latest information about available packages:

```bash
sudo apt update   # For Ubuntu/Debian
```

### Step 2: Install Nginx

Install Nginx using your package manager. For Ubuntu/Debian:

```bash
sudo apt install nginx
```

### Step 3: Start Nginx Service

After installation, start the Nginx service:

```bash
sudo systemctl start nginx
```

To enable Nginx to start on boot:

```bash
sudo systemctl enable nginx
```

### Step 4: Configure Firewall

If you have a firewall enabled, you may need to allow traffic on the default HTTP (port 80) and HTTPS (port 443) ports:

```bash
sudo ufw allow 80
sudo ufw allow 443
```

### Step 5: Create a Simple HTML Page

Create a simple HTML file to test your web server. For example:

```bash
echo "<html><body><h1>Hello, Nginx!</h1></body></html>" | sudo tee /var/www/html/index.html
```

### Step 6: Configure Nginx

Nginx configuration files are usually located in `/etc/nginx`. The main configuration file is `nginx.conf`, and server block configurations are typically in the `sites-available` directory.

Create a new server block configuration:

```bash
sudo nano /etc/nginx/sites-available/default
```

Replace the content with a basic configuration:

```nginx
server {
    listen 80;
    server_name your_domain_or_ip;

    location / {
        root /var/www/html;
        index index.html;
    }
}
```

Save the file and exit the text editor.

### Step 7: Test Nginx Configuration

Ensure your Nginx configuration is correct:

```bash
sudo nginx -t
```

If the test is successful, reload Nginx to apply the changes:

```bash
sudo systemctl reload nginx
```

### Step 8: Access the Web Server

Open a web browser and navigate to your server's IP address or domain name. You should see the "Hello, Nginx!" message.

Congratulations! You've successfully set up a basic web server using Nginx. Depending on your requirements, you can further customize the configuration to serve different types of content or host multiple websites.