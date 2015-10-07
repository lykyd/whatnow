# Dev Tool

## Git
**Init repo**
- echo "# howhard" >> README.md
- git init
- git add README.md
- git commit -m "first commit"
- git remote add origin https://github.com/Laudanum/howhard.git
- git push -u origin master

**Create branch**
- git branch experimental-d3 => create local branch
- git push -u origin experimental-d3 => create the remote branch
- git push -u origin develop => in the remote to commit to develop

**Delete branch**
- local: git branch -D develop.romain
- remote: git push origin --delete develop.romain

**Hotfix**
- checkout hotfix
- commit & push
- checkout master
- pull
- merge hotfix & push
- git tag 0.2.8
- git push —-tags
- checkout develop
- pull
- merge hotfix & push

**Cherry pick**
- git branch merge-request (create a branch where pick commits)
- git cherry-pick -n <commitnumber>
- git reset (unstage all commit change)
- git checkout (what you don’t want)
- git commit and push

**No Merge (display)**
- git branch —-no-merge

**Reset**
- git reset origin/branchname —-hard 

**Alias**
- git config --global alias.co checkout
- git config --unset alias.lg

**STASH**
- git stash list : display stash
- git stash pop : get last stash
- git stash : to stash everything that james said is not committed

**Checkout a commit number**
- git checkout 8948d4f (commit number)

**Match remote with local branch**
- git branch —-set-upstream-to=origin/remotebranch localbranch

## Command line

**File creation and edition**
- touch file : create
- less file : display
- nano file : write

**SSH connexion**
- ssh username@www.domain.com
- ping www.domain.com => domain accessible
- telnet www.domain.com 22 => check access to ssh port
- telnet www.domain.com 80 => check access to web server port
- 
**Rsync (connexion via ssh aux files)**
- rsync -vr -e “ssh -p numport” user@url-domain:dist/sources dist/local
- mysqldump dbname

**Secure copy (use ssh)**
- scp -P numport uname@urlname:/folder/file.sql ~/destination-folder/
- scp -r (folder and files inside)

**Permissions setup**
- groups : group that the user account belongs to
- chmod 755 file.ext

**MYSQL**
- mysqldump -uname -p dump.sql
- drop existing
- create schema
- mysql -uname -p dump.sql < db.sql

**Zip file**
- gzip file name

**Issue database**
- mv ib ibdata1.bak 
- cp -a ibdata1.bak ibdata1

**Import DB**
- USE database_name;
OR
- CREATE DATABASE database_name;
- USE database_name;

**Split DB**
- split -l 2000 ~/Desktop/dump.sql ~/Desktop/split_db/db-

**Screen**
- Ctrl+D, Ctrl+A
- screen -r pid (attache or detache)
- screen s NameofScreen
- screen ls (see the different jobs)
- Ctrl+D (kill the screen)

**GREP & TAIL**
- list of files: grep -Rl
- case insensitive: grep -i
or
- tail -f error.log (ctrl K to clean)

**DNS record**
- dig iloveclaude.com
- dig @ns1.registery iloveclaude.com (what this name server has for record)

**Direct message**
- ssh holly@wairarapa.local
- osascript -e 'display dialog "What?"'

**Restart Apache**
- sudo apachectl configtest &&  sudo apachectl restart

**Start Mysql**
- mysql -uroot
- mysql.server start

**Command shortcut**
- nano ~/.bash_profile
- source ~/.bash_profile
OR
- nano ~/.ssh/config

**Wget**
- wget --recursive --page-requisites --domains ozwayrealty.com.au --no-parent www.ozwayrealty.com.au/

**Patch**
- download .patch file
- patch -p1 < name.patch
OR
- git apply name.patch

**File/folder owner**
- sudo chown -R _www files/
_www: drupal
laudanum: user
root: ???

## Drush

- drush sql-dump > /destination/db.sql
- drush sql-dump -—result-file=dump.sql
- drush dl views --destination=profiles/myprofile/modules/views
- drush upwd --password="givememypasswordback" "admin" : reset password
- drush updb : update database
- drush dis <modulename> : disable module
- drush pm-list --type=Module --status=enabled : list module

## Angular
### The Service Recipe
--- root.js<br>
<pre>angular.module("root", ["services"])
	.controller("index", ["$scope", "multiplier",
		function ($scope, multiplier) {
			$scope.product = multiplier.multiply(2);
		}]);</pre>
		
--- services.js<br>
<pre>angular.module("services", [])
	.value("factor", 6)
	.service("multiplier", ["factor", Multiplier]);</pre>
	
--- multiplier.js<br>
<pre>function Multiplier(valueFactor) {
	this.multiply = function (controllerFactor) {
		return valueFactor * controllerFactor;
	};
}</pre>
