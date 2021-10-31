---
id: 988
name: "truatpasteurdotfr/singularity-docker-centos7-devtoolset"
branch: "master"
tag: "latest"
commit: "96db32aa408447189ad1187c63518fa8933e8d2b"
version: "c313f24e2ee6f75e65920e148241f18f"
build_date: "2019-11-07T00:52:49.487Z"
size_mb: 1943
size: 728113183
sif: "https://datasets.datalad.org/shub/truatpasteurdotfr/singularity-docker-centos7-devtoolset/latest/2019-11-07-96db32aa-c313f24e/c313f24e2ee6f75e65920e148241f18f.simg"
url: https://datasets.datalad.org/shub/truatpasteurdotfr/singularity-docker-centos7-devtoolset/latest/2019-11-07-96db32aa-c313f24e/
recipe: https://datasets.datalad.org/shub/truatpasteurdotfr/singularity-docker-centos7-devtoolset/latest/2019-11-07-96db32aa-c313f24e/Singularity
collection: truatpasteurdotfr/singularity-docker-centos7-devtoolset
---

# truatpasteurdotfr/singularity-docker-centos7-devtoolset:latest

```bash
$ singularity pull shub://truatpasteurdotfr/singularity-docker-centos7-devtoolset:latest
```

## Singularity Recipe

```singularity
BootStrap: docker
From: centos:centos7

%post
yum -y update && yum -y upgrade

# you need to create the top level directories since there is no overlay on CentOS-6
# specific to my setup
mkdir -p /local-storage /mnt/beegfs /baycells/home /baycells/scratch /c6/shared /c6/eb /local/gensoft2 /c6/shared/rpm /Bis/Scratch2 /mnt/beegfs /pasteur

# 
yum -y install centos-release-scl-rh epel-release
yum -y install htop

# 
yum -y install \
environment-modules \
acl.x86_64 \
adwaita-cursor-theme.noarch \
adwaita-icon-theme.noarch \
apr.x86_64 \
atk.x86_64 \
at-spi2-atk.x86_64 \
at-spi2-core.x86_64 \
audit-libs-python.x86_64 \
audit-libs.x86_64 \
autogen-libopts.x86_64 \
avahi-libs.x86_64 \
basesystem.noarch \
bash.x86_64 \
bc.x86_64 \
bind-libs-lite.x86_64 \
bind-license.noarch \
binutils.x86_64 \
boost-date-time.x86_64 \
boost-system.x86_64 \
boost-thread.x86_64 \
bsdcpio.x86_64 \
bzip2-libs.x86_64 \
ca-certificates.noarch \
cairo-devel.x86_64 \
cairo-gobject.x86_64 \
cairo.x86_64 \
centos-release.x86_64 \
checkpolicy.x86_64 \
chkconfig.x86_64 \
chrony.x86_64 \
cifs-utils.x86_64 \
cmake3-data.noarch \
cmake3.x86_64 \
cmake.x86_64 \
colord-libs.x86_64 \
coreutils.x86_64 \
cpio.x86_64 \
cpp.x86_64 \
cracklib-dicts.x86_64 \
cracklib.x86_64 \
cronie-noanacron.x86_64 \
cronie.x86_64 \
crontabs.noarch \
cryptsetup-libs.x86_64 \
cups-libs.x86_64 \
curl.x86_64 \
cyrus-sasl-lib.x86_64 \
dapl.x86_64 \
dbus-libs.x86_64 \
dbus.x86_64 \
dconf.x86_64 \
device-mapper-libs.x86_64 \
device-mapper.x86_64 \
devtoolset-3-binutils.x86_64 \
devtoolset-3-dwz.x86_64 \
devtoolset-3-dyninst.x86_64 \
devtoolset-3-elfutils-libelf.x86_64 \
devtoolset-3-elfutils-libs.x86_64 \
devtoolset-3-elfutils.x86_64 \
devtoolset-3-gcc-c++.x86_64 \
devtoolset-3-gcc-gfortran.x86_64 \
devtoolset-3-gcc.x86_64 \
devtoolset-3-gdb.x86_64 \
devtoolset-3-libquadmath-devel.x86_64 \
devtoolset-3-libstdc++-devel.x86_64 \
devtoolset-3-ltrace.x86_64 \
devtoolset-3-memstomp.x86_64 \
devtoolset-3-oprofile.x86_64 \
devtoolset-3-perftools.x86_64 \
devtoolset-3-runtime.x86_64 \
devtoolset-3-strace.x86_64 \
devtoolset-3-systemtap-client.x86_64 \
devtoolset-3-systemtap-devel.x86_64 \
devtoolset-3-systemtap-runtime.x86_64 \
devtoolset-3-systemtap.x86_64 \
devtoolset-3-toolchain.x86_64 \
devtoolset-3-valgrind.x86_64 \
devtoolset-4-binutils.x86_64 \
devtoolset-4-dwz.x86_64 \
devtoolset-4-dyninst.x86_64 \
devtoolset-4-elfutils-libelf.x86_64 \
devtoolset-4-elfutils-libs.x86_64 \
devtoolset-4-elfutils.x86_64 \
devtoolset-4-gcc-c++.x86_64 \
devtoolset-4-gcc-gfortran.x86_64 \
devtoolset-4-gcc.x86_64 \
devtoolset-4-gdb.x86_64 \
devtoolset-4-libquadmath-devel.x86_64 \
devtoolset-4-libstdc++-devel.x86_64 \
devtoolset-4-ltrace.x86_64 \
devtoolset-4-memstomp.x86_64 \
devtoolset-4-oprofile.x86_64 \
devtoolset-4-perftools.x86_64 \
devtoolset-4-runtime.x86_64 \
devtoolset-4-strace.x86_64 \
devtoolset-4-systemtap-client.x86_64 \
devtoolset-4-systemtap-devel.x86_64 \
devtoolset-4-systemtap-runtime.x86_64 \
devtoolset-4-systemtap.x86_64 \
devtoolset-4-toolchain.x86_64 \
devtoolset-4-valgrind.x86_64 \
devtoolset-6-binutils.x86_64 \
devtoolset-6-dwz.x86_64 \
devtoolset-6-dyninst.x86_64 \
devtoolset-6-elfutils-libelf.x86_64 \
devtoolset-6-elfutils-libs.x86_64 \
devtoolset-6-elfutils.x86_64 \
devtoolset-6-gcc-c++.x86_64 \
devtoolset-6-gcc-gfortran.x86_64 \
devtoolset-6-gcc.x86_64 \
devtoolset-6-gdb.x86_64 \
devtoolset-6-libquadmath-devel.x86_64 \
devtoolset-6-libstdc++-devel.x86_64 \
devtoolset-6-ltrace.x86_64 \
devtoolset-6-make.x86_64 \
devtoolset-6-memstomp.x86_64 \
devtoolset-6-oprofile.x86_64 \
devtoolset-6-perftools.x86_64 \
devtoolset-6-runtime.x86_64 \
devtoolset-6-strace.x86_64 \
devtoolset-6-systemtap-client.x86_64 \
devtoolset-6-systemtap-devel.x86_64 \
devtoolset-6-systemtap-runtime.x86_64 \
devtoolset-6-systemtap.x86_64 \
devtoolset-6-toolchain.x86_64 \
devtoolset-6-valgrind.x86_64 \
devtoolset-6.x86_64 \
devtoolset-7-binutils.x86_64 \
devtoolset-7-dwz.x86_64 \
devtoolset-7-dyninst.x86_64 \
devtoolset-7-elfutils-libelf.x86_64 \
devtoolset-7-elfutils-libs.x86_64 \
devtoolset-7-elfutils.x86_64 \
devtoolset-7-gcc-c++.x86_64 \
devtoolset-7-gcc-gfortran.x86_64 \
devtoolset-7-gcc.x86_64 \
devtoolset-7-gdb.x86_64 \
devtoolset-7-libquadmath-devel.x86_64 \
devtoolset-7-libstdc++-devel.x86_64 \
devtoolset-7-ltrace.x86_64 \
devtoolset-7-make.x86_64 \
devtoolset-7-memstomp.x86_64 \
devtoolset-7-oprofile.x86_64 \
devtoolset-7-perftools.x86_64 \
devtoolset-7-runtime.x86_64 \
devtoolset-7-strace.x86_64 \
devtoolset-7-systemtap-client.x86_64 \
devtoolset-7-systemtap-devel.x86_64 \
devtoolset-7-systemtap-runtime.x86_64 \
devtoolset-7-systemtap.x86_64 \
devtoolset-7-toolchain.x86_64 \
devtoolset-7-valgrind.x86_64 \
devtoolset-7.x86_64 \
dhclient.x86_64 \
dhcp-common.x86_64 \
dhcp-libs.x86_64 \
diffutils.x86_64 \
dracut.x86_64 \
e2fsprogs-libs.x86_64 \
e2fsprogs.x86_64 \
efivar-libs.x86_64 \
elfutils-default-yama-scope.noarch \
elfutils-libelf.x86_64 \
elfutils-libs.x86_64 \
emacs-filesystem.noarch \
ethtool.x86_64 \
expat-devel.x86_64 \
expat.x86_64 \
expect.x86_64 \
fftw-libs-double.x86_64 \
fftw-libs-single.x86_64 \
file-libs.x86_64 \
filesystem.x86_64 \
findutils.x86_64 \
fipscheck-lib.x86_64 \
fipscheck.x86_64 \
fontconfig-devel.x86_64 \
fontconfig.x86_64 \
fontpackages-filesystem.noarch \
freetype-devel.x86_64 \
freetype.x86_64 \
fuse-libs.x86_64 \
fuse-sshfs.x86_64 \
fuse.x86_64 \
gawk.x86_64 \
gcc-gfortran.x86_64 \
gcc.x86_64 \
gdbm.x86_64 \
gdk-pixbuf2.x86_64 \
gd.x86_64 \
GeoIP.x86_64 \
ghostscript-fonts.noarch \
ghostscript.x86_64 \
glib2-devel.x86_64 \
glib2.x86_64 \
glibc-common.x86_64 \
glibc-devel.x86_64 \
glibc-headers.x86_64 \
glibc.x86_64 \
glib-networking.x86_64 \
gl-manpages.noarch \
gmp.x86_64 \
gnupg2.x86_64 \
gnutls.x86_64 \
gpgme.x86_64 \
gpm-libs.x86_64 \
graphite2.x86_64 \
graphviz-tcl.x86_64 \
graphviz.x86_64 \
grep.x86_64 \
groff-base.x86_64 \
grubby.x86_64 \
gsettings-desktop-schemas.x86_64 \
gssproxy.x86_64 \
gtk2.x86_64 \
gtk3.x86_64 \
gtk-update-icon-cache.x86_64 \
gzip.x86_64 \
hardlink.x86_64 \
harfbuzz.x86_64 \
hicolor-icon-theme.noarch \
hostname.x86_64 \
htop.x86_64 \
hwdata.x86_64 \
hwloc-libs.x86_64 \
hwloc.x86_64 \
ibacm.x86_64 \
ibutils-libs.x86_64 \
ibutils.x86_64 \
infiniband-diags.x86_64 \
infinipath-psm.x86_64 \
info.x86_64 \
initscripts.x86_64 \
iproute.x86_64 \
iptables.x86_64 \
iputils.x86_64 \
iwpmd.x86_64 \
jasper-libs.x86_64 \
jbigkit-libs.x86_64 \
jsoncpp.x86_64 \
json-c.x86_64 \
json-glib.x86_64 \
kernel-devel.x86_64 \
kernel-headers.x86_64 \
keyutils-libs.x86_64 \
keyutils.x86_64 \
kpartx.x86_64 \
krb5-libs.x86_64 \
lcms2.x86_64 \
less.x86_64 \
lftp.x86_64 \
libacl.x86_64 \
libarchive.x86_64 \
libassuan.x86_64 \
libattr.x86_64 \
libbasicobjects.x86_64 \
libblkid.x86_64 \
libcap-ng.x86_64 \
libcap.x86_64 \
libcgroup.x86_64 \
libcollection.x86_64 \
libcom_err.x86_64 \
libconfuse.x86_64 \
libcroco.x86_64 \
libcurl.x86_64 \
libdb-utils.x86_64 \
libdb.x86_64 \
libdrm-devel.x86_64 \
libdrm.x86_64 \
libedit.x86_64 \
libepoxy.x86_64 \
libestr.x86_64 \
libevent.x86_64 \
libfastjson.x86_64 \
libffi.x86_64 \
libfontenc.x86_64 \
libgcc.x86_64 \
libgcrypt.x86_64 \
libgfortran4.x86_64 \
libgfortran.x86_64 \
libgomp.x86_64 \
libgpg-error.x86_64 \
libgusb.x86_64 \
libibcm.x86_64 \
libibmad.x86_64 \
libibumad.x86_64 \
libibverbs-utils.x86_64 \
libibverbs.x86_64 \
libICE.x86_64 \
libicu.x86_64 \
libidn.x86_64 \
libini_config.x86_64 \
libjpeg-turbo.x86_64 \
libldb.x86_64 \
libmng.x86_64 \
libmnl.x86_64 \
libmodman.x86_64 \
libmount.x86_64 \
libmpc.x86_64 \
libnetfilter_conntrack.x86_64 \
libnfnetlink.x86_64 \
libnfsidmap.x86_64 \
libnl3.x86_64 \
libpath_utils.x86_64 \
libpciaccess.x86_64 \
libpng-devel.x86_64 \
libpng.x86_64 \
libproxy.x86_64 \
libpwquality.x86_64 \
libquadmath-devel.x86_64 \
libquadmath.x86_64 \
librdmacm-utils.x86_64 \
librdmacm.x86_64 \
libref_array.x86_64 \
librsvg2.x86_64 \
libseccomp.x86_64 \
libselinux-python.x86_64 \
libselinux-utils.x86_64 \
libselinux.x86_64 \
libsemanage-python.x86_64 \
libsemanage.x86_64 \
libsepol.x86_64 \
libSM.x86_64 \
libsoup.x86_64 \
libssh2.x86_64 \
libss.x86_64 \
libstdc++.x86_64 \
libtalloc.x86_64 \
libtasn1.x86_64 \
libtdb.x86_64 \
libtevent.x86_64 \
libthai.x86_64 \
libtiff.x86_64 \
libtirpc.x86_64 \
libtool-ltdl.x86_64 \
libunwind.x86_64 \
libusbx.x86_64 \
libuser.x86_64 \
libutempter.x86_64 \
libuuid.x86_64 \
libverto-libevent.x86_64 \
libverto.x86_64 \
libwbclient.x86_64 \
libX11-common.noarch \
libX11-devel.x86_64 \
libX11.x86_64 \
libXau-devel.x86_64 \
libXau.x86_64 \
libXaw.x86_64 \
libxcb-devel.x86_64 \
libxcb.x86_64 \
libXcomposite.x86_64 \
libXcursor.x86_64 \
libXdamage-devel.x86_64 \
libXdamage.x86_64 \
libXdmcp.x86_64 \
libXext-devel.x86_64 \
libXext.x86_64 \
libXfixes-devel.x86_64 \
libXfixes.x86_64 \
libXfont2.x86_64 \
libXfont.x86_64 \
libXft.x86_64 \
libXinerama.x86_64 \
libXi.x86_64 \
libxkbfile.x86_64 \
libxml2.x86_64 \
libXmu.x86_64 \
libXpm.x86_64 \
libXrandr.x86_64 \
libXrender-devel.x86_64 \
libXrender.x86_64 \
libxshmfence.x86_64 \
libXtst.x86_64 \
libXt.x86_64 \
libXxf86vm-devel.x86_64 \
libXxf86vm.x86_64 \
linux-firmware.noarch \
logrotate.x86_64 \
lua.x86_64 \
lyx-fonts.noarch \
lzo.x86_64 \
make.x86_64 \
mariadb-libs.x86_64 \
mesa-libEGL-devel.x86_64 \
mesa-libEGL.x86_64 \
mesa-libgbm.x86_64 \
mesa-libglapi.x86_64 \
mesa-libGL-devel.x86_64 \
mesa-libGL.x86_64 \
mokutil.x86_64 \
mpfr.x86_64 \
mstflint.x86_64 \
nano.x86_64 \
ncurses-base.noarch \
ncurses-libs.x86_64 \
ncurses.x86_64 \
nettle.x86_64 \
net-tools.x86_64 \
nfs-utils.x86_64 \
nspr.x86_64 \
nss-pem.x86_64 \
nss-softokn-freebl.x86_64 \
nss-softokn.x86_64 \
nss-sysinit.x86_64 \
nss-tools.x86_64 \
nss-util.x86_64 \
nss.x86_64 \
ntpdate.x86_64 \
ntp.x86_64 \
numactl-libs.x86_64 \
numactl.x86_64 \
opa-address-resolution.x86_64 \
opa-basic-tools.x86_64 \
opa-fastfabric.x86_64 \
openldap.x86_64 \
opensm-libs.x86_64 \
openssh-clients.x86_64 \
openssh-server.x86_64 \
openssh.x86_64 \
openssl-libs.x86_64 \
p11-kit-trust.x86_64 \
p11-kit.x86_64 \
pam.x86_64 \
pango.x86_64 \
pciutils-libs.x86_64 \
pciutils.x86_64 \
pcre-devel.x86_64 \
pcre.x86_64 \
perftest.x86_64 \
perl-Carp.noarch \
perl-constant.noarch \
perl-Encode.x86_64 \
perl-Exporter.noarch \
perl-File-Path.noarch \
perl-File-Temp.noarch \
perl-Filter.x86_64 \
perl-Getopt-Long.noarch \
perl-HTTP-Tiny.noarch \
perl-libs.x86_64 \
perl-macros.x86_64 \
perl-parent.noarch \
perl-PathTools.x86_64 \
perl-Pod-Escapes.noarch \
perl-podlators.noarch \
perl-Pod-Perldoc.noarch \
perl-Pod-Simple.noarch \
perl-Pod-Usage.noarch \
perl-Scalar-List-Utils.x86_64 \
perl-Socket.x86_64 \
perl-Storable.x86_64 \
perl-Text-ParseWords.noarch \
perl-threads-shared.x86_64 \
perl-threads.x86_64 \
perl-Time-HiRes.x86_64 \
perl-Time-Local.noarch \
perl.x86_64 \
pinentry.x86_64 \
pixman-devel.x86_64 \
pixman.x86_64 \
pkgconfig.x86_64 \
policycoreutils-python.x86_64 \
policycoreutils.x86_64 \
poppler-data.noarch \
popt.x86_64 \
postfix.x86_64 \
procps-ng.x86_64 \
psmisc.x86_64 \
pth.x86_64 \
pygpgme.x86_64 \
pyliblzma.x86_64 \
python-iniparse.noarch \
python-IPy.noarch \
python-libs.x86_64 \
python-pycurl.x86_64 \
python-urlgrabber.noarch \
python.x86_64 \
pyxattr.x86_64 \
qperf.x86_64 \
qrencode-libs.x86_64 \
qt-settings.noarch \
qt-x11.x86_64 \
qt.x86_64 \
quota-nls.noarch \
quota.x86_64 \
rdate.x86_64 \
rdma-core.x86_64 \
readline.x86_64 \
rest.x86_64 \
rpcbind.x86_64 \
rpm-build-libs.x86_64 \
rpm-libs.x86_64 \
rpm-python.x86_64 \
rpm.x86_64 \
rsync.x86_64 \
rsyslog.x86_64 \
samba-client-libs.x86_64 \
samba-common.noarch \
scl-utils.x86_64 \
screen.x86_64 \
sed.x86_64 \
setools-libs.x86_64 \
setup.noarch \
shadow-utils.x86_64 \
shared-mime-info.x86_64 \
singularity-runtime.x86_64 \
singularity.x86_64 \
sqlite.x86_64 \
squashfs-tools.x86_64 \
srp_daemon.x86_64 \
strace.x86_64 \
sudo.x86_64 \
swig.x86_64 \
systemd-libs.x86_64 \
systemd-sysv.x86_64 \
systemd.x86_64 \
sysvinit-tools.x86_64 \
tar.x86_64 \
tcl.x86_64 \
tcp_wrappers-libs.x86_64 \
tcp_wrappers.x86_64 \
tcsh.x86_64 \
tk.x86_64 \
tmux.x86_64 \
trousers.x86_64 \
tzdata.noarch \
unzip.x86_64 \
urw-fonts.noarch \
ustr.x86_64 \
util-linux.x86_64 \
vim-common.x86_64 \
vim-enhanced.x86_64 \
vim-filesystem.x86_64 \
vim-minimal.x86_64 \
wget.x86_64 \
which.x86_64 \
words.noarch \
xkeyboard-config.noarch \
xorg-x11-font-utils.x86_64 \
xorg-x11-proto-devel.noarch \
xorg-x11-server-common.x86_64 \
xorg-x11-server-Xorg.x86_64 \
xorg-x11-xkb-utils.x86_64 \
xz-libs.x86_64 \
xz.x86_64 \
zip.x86_64 \
zlib-devel.x86_64 \
zlib.x86_64


%runscript
    echo "Running bash -l in the container"
    echo "use 'scl -l' to list and 'scl enable devtoolset-N bash' to activate SCL devtoolset-N"
    bash -l
```

## Collection

 - Name: [truatpasteurdotfr/singularity-docker-centos7-devtoolset](https://github.com/truatpasteurdotfr/singularity-docker-centos7-devtoolset)
 - License: None
