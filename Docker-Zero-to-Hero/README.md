# 🐳 Docker – Day 1: Setting Up Docker on Mac M1 using Multipass 💻🚀

## 📘 Overview

This is **Day 1** of my 7-Day Docker Learning Challenge!*
Since I’m using a **MacBook M1** and don’t currently have any active **cloud subscriptions**, I decided to set up an **Ubuntu environment using Multipass** — a lightweight virtualization tool by Canonical.

This setup provides an isolated and Linux-native environment to experiment with Docker safely.

---

## 🧩 Step 1: Install Multipass

Multipass allows you to launch Ubuntu VMs on macOS easily.
Install it via **Homebrew**:

```bash
brew install --cask multipass
```

✅ **Note:** Homebrew simplifies package installations on macOS.

<img width="2880" height="382" alt="Pasted Graphic" src="https://github.com/user-attachments/assets/27dc0d52-3a0a-49fb-be4b-dc74e06a38e8" />


---

## 🐧 Step 2: Launch an Ubuntu Instance

Once Multipass is installed, create a new Ubuntu virtual machine (VM):

```bash
multipass launch --name ubuntu --memory 2G --disk 10G
```

💡 This command creates a VM named **ubuntu**, allocating:

* **2 GB** of memory
* **10 GB** of disk space



---

## 🔑 Step 3: Access the Ubuntu VM

After the VM is launched, access it using:

```bash
multipass shell ubuntu
```

This command opens an interactive shell session inside the Ubuntu VM.
Now you’re ready to install and configure Docker in a true Linux environment!

<img width="1096" height="1004" alt="Sais-MacBook-Airado sai$ multipass launch --name ubuntu" src="https://github.com/user-attachments/assets/0c206546-cb30-404d-9362-1035a8122902" />


---

## 🔐 Step 4: Add User Permissions for Docker

Docker commands typically require **root privileges**.
To simplify usage, you can add your Ubuntu user to the **Docker group**.

In my setup, I’m adding the default `ubuntu` user:

```bash
sudo usermod -aG docker ubuntu
```

🧠 **Why this step?**
It allows running Docker commands without needing `sudo` every time.

⚠️ **Important:**
After adding the user, **log out and log back in** for changes to take effect.

<img width="1450" height="54" alt="Pasted Graphic 4" src="https://github.com/user-attachments/assets/bde043a7-cc3d-4b4f-a8df-804e534a03a5" />


---

## 🏗️ Step 5: Build a Docker Image

Now that Docker is ready, navigate to the path containing your **Dockerfile**.
In my case, it’s inside my GitHub repository.

Once inside the directory, build your image:

```bash
docker build -t sai7713/myimage:latest .
```

🧩 **Explanation:**

* `-t sai7713/myimage:latest` → tags the image as `latest` (you can use `0.0.1` or any custom tag)
* The `.` at the end tells Docker to use the Dockerfile in the current directory

<img width="710" height="64" alt="Successfully built 940b925feafa" src="https://github.com/user-attachments/assets/4bfeb1ec-a690-4a34-9f12-99d42da07ae2" />


---

## ▶️ Step 6: Run the Docker Image

After building the image, run it to verify everything works correctly:

```bash
docker run sai7713/myimage:latest
```

In my case, this executed a small Python snippet inside the container successfully. 🎉

<img width="1404" height="62" alt="Pasted Graphic 1" src="https://github.com/user-attachments/assets/dac9b729-624d-4af1-b2ba-ec6457e28dc4" />


---

## 🗂️ Step 7: View Available Images

To list all the Docker images on your system:

```bash
docker images
```

You’ll see details such as the **repository name**, **tag**, **image ID**, and **size**.

<img width="1404" height="114" alt="Pasted Graphic 2" src="https://github.com/user-attachments/assets/2621f45b-c852-482d-913c-62b32b39d5bc" />


---

## ☁️ Step 8: Push Image to Docker Hub

Once your image is tested, you can share it or store it in your **Docker Hub** account.

### Step 8.1 — Create a Docker Access Token

1. Go to **[Docker Hub → Account Settings → Security]**
2. Click **New Access Token**
3. Give it a recognizable name (e.g., `macm1-login` or `azurevm-login`)
4. Copy the generated token securely — it acts as your password for CLI logins

📸 *[Insert Screenshot – Docker Hub access token creation]*

### Step 8.2 — Login Using Token

Authenticate your Docker CLI with your Docker Hub account using the token:

```bash
echo "YOUR_TOKEN_HERE" | docker login -u "sai7713" --password-stdin
```

---

### Step 8.3 — Push the Image

Finally, push your Docker image to Docker Hub:

```bash
docker push sai7713/myimage:latest
```

Once pushed, it will be available publicly under your Docker Hub repository! 🌍

<img width="1456" height="204" alt="Pasted Graphic 3" src="https://github.com/user-attachments/assets/cef27da3-334d-492d-a0c5-2a9f08d44014" />


---

## 💡 Key Takeaways

✅ **Multipass** provides a clean and lightweight Ubuntu environment on macOS.
✅ **Adding user permissions** simplifies Docker usage without constant `sudo`.
✅ **Docker images** are tagged and versioned for easy management and sharing.
✅ **Pushing to Docker Hub** allows you to reuse and share your images anywhere.

---

## 🚀 **Day 1 Summary**

* Set up Multipass on Mac M1
* Created and accessed an Ubuntu VM
* Installed and configured Docker
* Built, ran, and pushed my first Docker image!
---


