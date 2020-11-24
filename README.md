Run this to clear postfix queue

mkdir /root/
cd /root/
sudo wget https://raw.githubusercontent.com/davidfrosty0001/smtp/main/defer.sh /root/defer.sh
sudo wget https://raw.githubusercontent.com/davidfrosty0001/smtp/main/deferall.sh /root/deferall.sh
sudo chmod u+x /root/deferall.sh
sudo chmod u+x /root/defer.sh
sudo crontab -l | { cat; echo "5 * * * * /root/defer.sh"; } | crontab -
sudo crontab -l | { cat; echo "0 */4 * * * /usr/sbin/reboot"; } | crontab -
sudo crontab -l | { cat; echo "0 */12 * * * /root/deferall.sh"; } | crontab -
