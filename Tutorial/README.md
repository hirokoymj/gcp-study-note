# VM Startup script

**Links:**

-[6. Running Startup Scripts in VMs | Google Cloud Quick Tutorials](https://www.youtube.com/watch?v=IYYg4ogb4k0&list=PLuJRcdtonlDAN73rZsRk_eiJ0NU9h1Cms&index=8)

- https://github.com/drehnstrom/space-invaders

startup script

```
#! /bin/bash

apt update
apt install -y git apache2
cd /var/www/html
rm index.html -f
git init
git pull https://github.com/drehnstrom/space-invaders
```
