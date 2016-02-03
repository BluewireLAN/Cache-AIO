# Cache-AIO

BSD CLI:
sysctl kern.ipc.somaxconn=4096

DISK RAAID:
mkdir /data
kldload geom_stripe
gstripe label -v st0 /dev/ada0 /dev/ada1 /dev/ada2
bsdlabel -wB /dev/stripe/st0
newfs -U /dev/stripe/st0a
mount /dev/stripe/st0a /data
echo "/dev/stripe/st0a /data ufs rw 2 2" >> /etc/fstab
echo 'geom_stripe_load="YES"' >> /boot/loader.conf