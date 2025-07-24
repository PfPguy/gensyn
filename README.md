# Gensyn RL-Swarm Basic Setup


## Platform you can use for GPU 

**VAST** = https://cloud.vast.ai/?ref_id=234200

**QUICKPOD** = https://console.quickpod.io?affiliate=e683292b-f79c-4839-aa94-3feaabc35ee0

---

## **STEP 1 (For BOTH CPU & GPU):**

Run this **one-liner command** to update your system, install all dependencies, set up Node.js & Yarn, and clone RL-Swarm:

```bash
apt update && apt upgrade -y && apt install -y screen curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip python3 python3-pip python3-venv python3-dev && curl -fsSL https://deb.nodesource.com/setup_22.x | bash - && apt install -y nodejs && npm install -g yarn && curl -o- -L https://yarnpkg.com/install.sh | bash && export PATH="$HOME/.yarn/bin:$HOME/.config/yarn/global/node_modules/.bin:$PATH" && source ~/.bashrc && git clone https://github.com/gensyn-ai/rl-swarm/
```

## **STEP 2 (For BOTH CPU & GPU):**

Create a **new screen session** and start RL-Swarm:
```bash
screen -S gensyn
```
Once you are inside the new screen, run these commands:
```bash
cd rl-swarm/
python3 -m venv .venv
source .venv/bin/activate
./run_rl_swarm.sh
```

✅ If it throws any error:
Copy the full error message and paste it into ChatGPT, asking for the correct command. (Usually this runs without any errors.)

Till then **DETACH THE SCREEN** : BY PRESSING CTRL+A+D together or one by one


## **STEP 3: Start LocalTunnel in Another Screen**
```bash
screen -S login
```

Ones again you will get into the new screen run these command :
```bash
npm install -g localtunnel
curl https://loca.lt/mytunnelpassword
lt --port 3000
```
**COPY THE IP ADDRRESS IT SHOWS AND OPEN THE LINK IT SHOWS BY PRESSING CRTL + RIGHT CLICK (ON MOUSE )**

Then **DETACH THE SCREEN** : BY PRESSING CTRL+A+D together or one by one

NOW you need you reactech the screen you detached previously for that 
```bash
screen -ls
```
You should see two screens named login and gensyn with digits before them.

## ✅ To reattach the RL-Swarm screen:
**(DO NOT COPY THIS EXACTLY — replace <digit> yes you have to remove tis also <> while replacing with the actual number shown in screen list)**
```bash
screen -R <digit>.gensyn

```

## STEP 5: Final Steps

1 Head back to the page we opened earlier.

2 Paste the IP address we copy earlier .

3 Login with your Gmail account.

4 Head back to terminal 

5 Wait a few minutes until you see the Y/N option — choose N.

6 Finally, select the model you want to run from the list.

## ✅ Supported Models & Recommendations

You can just click ENTER if you want to systme will auto pick the best Model for you 


``` Gensyn/Qwen2.5-0.5B-Instruct ``` → Best for CPU or 12–16GB VRAM GPUs

```Qwen/Qwen3-0.6B ```→ Best for RTX 3090 & 4090

```nvidia/AceInstruct-1.5B``` → Ideal for A100 & H200

```dnotitia/Smoothie-Qwen3-1.7B ```→ Needs 32GB VRAM GPU or higher

```Gensyn/Qwen2.5-1.5B-Instruct``` → Works on 4090 (with tweaks) but 32GB VRAM recommended
