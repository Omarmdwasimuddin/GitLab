# Module 02 — Local Machine এ GitLab Install (Docker দিয়ে)

**Prerequisite:** তোমার machine এ Docker install থাকতে হবে (তুমি Docker experience already রাখো তোমার stack এ, তাই এটা সহজ)।

## কেন Docker দিয়েই install করব?

GitLab CE কে raw ভাবে (bare metal) install করা অনেক ভারী এবং complex process (Ruby, PostgreSQL, Redis, Nginx — সব আলাদা আলাদা setup লাগে)। Docker দিয়ে করলে official GitLab image ব্যবহার করে সব কিছু এক container এ পাওয়া যায় — এটাই industry standard approach for local/dev setup।

---

# Step-by-step (Micro Detail)

## Step 1 — একটা directory বানাও যেখানে GitLab এর data persist থাকবে:

```bash
mkdir -p ~/gitlab/config ~/gitlab/logs ~/gitlab/data
```

এই তিনটা folder কেন লাগবে সেটা বুঝে নাও:

- `config` → GitLab এর সব configuration file (`gitlab.rb` ইত্যাদি)
- `logs` → সব log file, যেটা error debug করতে কাজে লাগবে
- `data` → actual database, repositories — এটাই সবচেয়ে গুরুত্বপূর্ণ, container বন্ধ/delete হয়ে গেলেও data safe থাকে

---

## Step 2 — GitLab CE container রান করো:

```bash
sudo docker run --detach \
  --hostname localhost \
  --publish 8929:8929 --publish 2224:22 \
  --name gitlab \
  --restart always \
  --volume ~/gitlab/config:/etc/gitlab \
  --volume ~/gitlab/logs:/var/log/gitlab \
  --volume ~/gitlab/data:/var/opt/gitlab \
  --shm-size 256m \
  gitlab/gitlab-ce:latest
```

এখন প্রতিটা flag কী করছে, একটা একটা করে বুঝি (এটাই "micro info"):

- `--detach` → background এ চলবে, terminal block হবে না
- `--hostname localhost` → GitLab internally এই hostname দিয়ে নিজের URL বানায়
- `--publish 8929:8929` → GitLab এর web UI host machine এর 8929 port এ পাওয়া যাবে (তুমি browser এ `http://localhost:8929` দিয়ে ঢুকবে)
- `--publish 2224:22` → SSH দিয়ে git push/pull করার জন্য port mapping (container এর 22 default SSH port, host এর 2224 এ map করা হলো কারণ 22 সাধারণত host machine এ আগে থেকেই ব্যবহৃত থাকে)
- `--name gitlab` → container এর নাম, পরে `docker stop gitlab`, `docker logs gitlab` এভাবে refer করতে সুবিধা হবে
- `--restart always` → machine reboot হলেও GitLab auto-start হবে
- `--volume` তিনটা → আগে বানানো folder গুলো container এর ভিতরের path এর সাথে mount করা, যাতে data persist থাকে
- `--shm-size 256m` → shared memory size বাড়ানো, না হলে GitLab এর কিছু internal process (PostgreSQL) crash করতে পারে
- `gitlab/gitlab-ce:latest` → official Docker image

---

## Step 3 — GitLab পুরোপুরি start হতে সময় লাগবে (2-5 মিনিট)। Status check করো:

```bash
sudo docker logs -f gitlab
```

যখন দেখবে log এ কিছুক্ষণ নতুন কিছু print হচ্ছে না এবং `"gitlab Reconfigured!"` এর মতো message এসেছে, তখন ready।

---

## Step 4 — Browser এ ঢোকো:

```text
http://localhost:8929
```

প্রথমবার ঢুকলে GitLab তোমাকে root user এর password set করতে বলবে (initial signup screen)। Username হবে `root`।

যদি সরাসরি password set করার screen না দেখাও, initial random password বের করার command:

```bash
sudo docker exec -it gitlab grep 'Password:' /etc/gitlab/initial_root_password
```

(এই password প্রথম 24 ঘন্টা valid থাকে, তারপর file auto-delete হয়ে যায় — তাই প্রথমবারেই login করে নিজের password set করে নেওয়া ভালো অভ্যাস)
