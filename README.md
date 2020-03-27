# zimbra-ui
 
This Zimbra Universal UI was obtained from Unofficial Zimbra 8.8.5 that created by Zeta Alliance. I am copying zimbra folder from webapps and save into my Github. This Zimbra Universal UI have been tested by me on Zimbra 8.8.12/8.8.15 and working properly. If you want to try installing this Zimbra Universal UI on your Zimbra, please try the guide below
Backup Zimbra folder from webapps

cd /opt/zimbra/jetty/webapps/
tar -czvf /srv/zimbra-webapps.tgz zimbra

The backup file will save in the /srv/ folder
Download Zimbra Universal UI

cd /tmp/
wget -c https://github.com/lionesia/zimbra-ui/raw/master/zimbra-ui.tgz

Extract and Rsync

tar -zxvf zimbra-ui.tgz
rsync -avP /tmp/zimbra/ /opt/zimbra/jetty/webapps/zimbra/

Remove harmony themes and replace with Universal UI themes

Zimbra using harmony as default themes for webmail

cd /opt/zimbra/jetty/webapps/zimbra/skins/
rm -rvf harmony/
ln -sf clarity harmony

If there are other users who use special themes, you can delete and replace them with Universal UI themes
Fixperms and Restart Zimbra Mailbox

/opt/zimbra/libexec/zmfixperms -v
su - zimbra -c "zmmailboxdctl restart"
