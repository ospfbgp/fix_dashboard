# Make dashboard root directory
<pre>
cd ~
sudo bash
rm -fr fix_dashboard/
git clone https://github.com/ospfbgp/fix_dashboard.git
cp ~/fix_dashboard/dashboard.conf /etc/apache2/sites-available/.
cp ~/fix_dashboard/dashboard-ssl.conf /etc/apache2/sites-available/.
chown root:root /etc/apache2/sites-available/dashboard*.conf
chmod 644 /etc/apache2/sites-available/dashboard*.conf

cp ~/fix_dashboard/favicon-16x16.png /opt/www/images/.
cp ~/fix_dashboard/favicon-32x32.png /opt/www/images/.
cp ~/fix_dashboard/favicon.ico /opt/www/images/.
cp ~/fix_dashboard/logo.png /opt/www/images/.
cp ~/fix_dashboard/stepcg_logo.png /opt/www/images/.
chown stepcg:stepcg /opt/www/images/*
chmod 644 /opt/www/images/*

cp ~/fix_dashboard/index.html /opt/www/.
chown stepcg:stepcg /opt/www/index.html
chmod 644 /opt/www/images/index.html

cp ~/fix_dashboard/librenms /etc/cron.d/.
chown root:root /etc/cron.d/librenms
chmod 644 /etc/cron.d/librenms

cp ~/fix_dashboard/.htaccess /opt/librenms/html/.
chown -R librenms:librenms /opt/librenms
chmod 770 /opt/librenms
setfacl -d -m g::rwx /opt/librenms/rrd /opt/librenms/logs /opt/librenms/bootstrap/cache/ /opt/librenms/storage/
setfacl -R -m g::rwx /opt/librenms/rrd /opt/librenms/logs /opt/librenms/bootstrap/cache/ /opt/librenms/storage/
</pre>
# execute service apache2 restart 
# edit file /opt/librenms/config.php and remove $config['base_url']
# execute script /opt/librenms/daily.sh
