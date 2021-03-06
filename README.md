# README.md

This app will send predictions to end-users.

The end-user should enter a stock symbol.

Then, the app will display a prediction for 2017.

I should follow some steps to start development on this app:

- Download this OVA file:
- https://drive.google.com/open?id=0Bx3iDDAtxxI4WWFpemh2ZjViVkk
- import it into Virtual Box
- Start it
- Login as ann with password a
- Then...

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove

sudo apt-get install autoconf bison build-essential libssl-dev libyaml-dev \
libreadline6-dev zlib1g-dev libncurses5-dev libffi-dev libgdbm3       \
libgdbm-dev libsqlite3-dev gitk postgresql postgresql-server-dev-all  \
libpq-dev emacs wget curl chromium-browser openssh-server aptitude    \
ruby ruby-dev sqlite3 r-base r-base-dev

shutdown -r now
```

- After reboot, I should login as ann
- Then...

```
sudo su - postgres
psql
```

- Then...

```sql
create role ann with login superuser password 'a2';
create database ann;
create database dev;
create database tst;
create database prd;
\q
exit
```

- See if ann can connect:

```
psql -aP pager=no -U ann -W dev
```

- Try this:

```sql
create table dropme(c1 int);
drop   table dropme;
\q
```

- Next I should clone the repository:

```bash
cd ~ann
git clone https://github.com/danbikle/predict2017
```

- Then I should create some DB tables:

```bash
cd ~ann/predict2017
bundle install
bin/rails db:migrate
```

- If I want to run the webserver on my laptop I should run these shell commands:

```bash
cd ~ann/predict2017
script/railss.bash
```

- Next, I should create an account at heroku.com using their website.

- Then I should enter shell commands:

```bash
cd ~ann/predict2017
heroku auth:login
heroku create
git push heroku master
heroku run bin/rails db:migrate
```

- Then I should visit the app at herokuapp.com.

- Or you can visit mine:

https://predict2017.herokuapp.com





