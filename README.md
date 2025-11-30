# cyber-shield
Siber Olay Müdahale İstasyonu – Cyber Shield Projesi
sudo groupadd analysts
sudo chown root:analysts evidence
sudo chmod 750 evidence

sudo setfacl -m g:analysts:r-x evidence
sudo setfacl -m o::--- evidence

sudo setfacl -d -m g:analysts:r-x evidence
sudo setfacl -d -m o::--- evidence
