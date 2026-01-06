# This update for Arix already includes add-ons, I can't delete it because there are too many, if you are a pro in PHP maybe you can delete it manually 


1. I don't know if you are using localhost or VPS directly, I assume you have installed Pterodactyl on your VPS without using any other themes or add-ons, 

- First move arix.zip into your pterodactyl folder on your VPS, 

2. run this
```bash
cd /var/www/pterodactyl
```
```bash
unzip -o arix.zip
cp -R arix/* .
cp -R arix/.* . 2>/dev/null
rm -rf arix
```
- The above commands will unzip arix and copy the contents of all files in the arix folder. then delete it

3. install nodejs if you haven't installed it yet
```bash
curl -sL https://deb.nodesource.com/setup_22.x | sudo -E bash -
apt-get install -y nodejs
```

4. install yarn
```bash
npm install -g yarn
```

5. install library
```bash
yarn install
```
```bash
yarn add react-paypal-checkout-button @paypal/paypal-js
```

- why is there a paypal library? because as I said before it is already integrated with add-ons, and that's for billing add-ons

6. run build
```bash
NODE_OPTIONS=--openssl-legacy-provider yarn run build:production
```

7. migrate database
```bash
php artisan migrate --force
```

8. clear cache
```bash
php artisan optimize:clear
```
9. allow perms
```bash
chown -R www-data:www-data /var/www/pterodactyl/*
chmod -R 755 storage
```

Just like that, easy right?, 

- I remind you this is only for users who have just installed pterodactyl - try not to install any other add-ons or themes first

- and one more thing there is a reverse proxy add-on, If you want to setup it, make sure you understand the GO language, because of that you have to edit the wings section manually

- or you can join my discord server https://discord.gg/aerox