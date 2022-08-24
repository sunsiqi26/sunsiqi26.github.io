$url = $_GET['url'];
if (strpos($url, 'var')!==false || strpos($url, 'www') !== false || strpos($url, 'html')!==false ){
	exit('hacker');
}

if (strpos($url, 'http'!==false)){
	exit('no network, try other protocol');
}
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, FALSE);
curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, FALSE);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
$output = curl_exec($ch);
curl_close($ch);
var_dump($output);

$hint="Anyway,`root passwd` in /etc somewhere(in a code annotation, find it and login as root to do more; give you a shell in ccccCmd.php";
"

etc
```
adduser.conf
alternatives
apache2
apt
bash.bashrc
bindresvport.blacklist
ca-certificates
ca-certificates.conf
cron.daily
debconf.conf
debian_version
default
deluser.conf
dpkg
emacs
environment
fstab
gai.conf
group
group-
gshadow
gss
host.conf
hostname
hosts
init.d
inputrc
issue
issue.net
kernel
ld.so.cache
ld.so.conf
ld.so.conf.d
ldap
libaudit.conf
localtime
login.defs
logrotate.d
magic
magic.mime
mailcap
mailcap.order
mime.types
mke2fs.conf
motd
mtab
nsswitch.conf
opt
os-release
pam.conf
pam.d
passwd
passwd-
perl
profile
profile.d
rc0.d
rc1.d
rc2.d
rc3.d
rc4.d
rc5.d
rc6.d
rcS.d
resolv.conf
rmt
securetty
security
selinux
shadow
shadow-
shells
skel
ssl
subgid
subuid
sysctl.conf
sysctl.d
systemd
terminfo
test
timezone
update-motd.d
vim
xattr.conf
```