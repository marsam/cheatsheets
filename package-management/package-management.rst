
=============================
Package Management Cheatsheet
=============================
A package management reference card for Linux distributions and FreeBSD
=======================================================================

.. :Authors: DistroWatch.com (http://distrowatch.com/packages.php); Mario Rodas (pdf version)

Introduction
------------
Package management is probably the most distinctive feature of any Linux
distribution. While the current trend among most of the major projects is to
offer some sort of a clickable interface where users can select a package and
install it with a mouse click (e.g. Debian's Synaptic or Mandriva's Drakrpm),
these types of programs are generally just graphical front-ends to the
low-level utilities that manage the tasks associated with installing packages
on a Linux system. And even though many desktop Linux users feel much more
comfortable installing packages through these intuitive graphical tools,
there is no denying that command-line package management offers two excellent
features not available in any graphical package management utility: power and
speed.

One problem that many distro-hoppers and operating system enthusiasts
encounter is having to master (or relearn) a set of package management
commands each time they switch from one distribution group to another.
Additionally, the package management tools tend to evolve, with new features
and even new commands added to every new version. This is why we created this
package management cheatsheet - an easy reference card covering most
frequently used package management tasks in Linux distributions and FreeBSD.
As always, we welcome corrections, updates and suggestions - if you spot any
error or wish to have another package management utility added to this page,
feel free to contact us (email address at the bottom of this page). 

.. Package Management Cheatsheet

Cheatsheet
-----------------------------

Main distributions
++++++++++++++++++
The first table lists package management tasks in the four most popular
distribution groups - `Debian`_ (including `Ubuntu`_, Linux `Mint`_,
`KNOPPIX`_, `sidux`_ and other Debian derivatives), `openSUSE`_, `Fedora`_
(including `Red Hat`_ Enterprise Linux, `CentOS`_, `Scientific`_ Linux and
other Fedora-based distributions), and `Mandriva`_ Linux.

.. _Debian: http://distrowatch.com/debian
.. _Ubuntu: http://distrowatch.com/ubuntu
.. _Mint: http://distrowatch.com/mint
.. _KNOPPIX: http://distrowatch.com/knoppix
.. _sidux: http://distrowatch.com/sidux
.. _openSUSE: http://distrowatch.com/suse
.. _Fedora: http://distrowatch.com/fedora
.. _Red Hat: http://distrowatch.com/redhat
.. _CentOS: http://distrowatch.com/centos 
.. _Scientific: http://distrowatch.com/scientific
.. _Mandriva: http://distrowatch.com/mandriva

+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| Task                    | apt (deb) Debian, Ubuntu      | zypp (rpm) openSUSE       | yum (rpm) Fedora,      | urpmi (rpm) Mandriva       |
|                         |                               |                           | CentOS                 |                            |
+=========================+===============================+===========================+========================+============================+
| **Managing software**                                                                                                                     |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| Install new software    | apt-get install *pkg*         | zypper install *pkg*      | yum install *pkg*      | urpmi *pkg*                |
| from package repository |                               |                           |                        |                            |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| Install new software    | dpkg -i *pkg*                 | zypper install *pkg*      | yum localinstall *pkg* | urpmi *pkg*                |
| from package file       |                               |                           |                        |                            |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| Update existing         | apt-get install *pkg*         | zypper update -t          | yum update *pkg*       | urpmi *pkg*                |
| software                |                               | package *pkg*             |                        |                            |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| Remove unwanted         | apt-get remove *pkg*          | zypper remove *pkg*       | yum erase *pkg*        | urpme *pkg*                |
| software                |                               |                           |                        |                            |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| **Updating the system**                                                                                                                   |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| Update package list     | apt-get update                | zypper refresh            | yum check-update       | urpmi.update -a            |
|                         | aptitude update               |                           |                        |                            |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| Update system           | apt-get upgrade               | zypper update             | yum update             | urpmi --auto-select        |
|                         | aptitude safe-upgrade         |                           |                        |                            |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| **Searching for packages**                                                                                                                |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| Search by package name  | apt-cache search *pkg*        | zypper search *pkg*       | yum list *pkg*         | urpmq *pkg*                |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| Search by pattern       | apt-cache search *pattern*    | zypper search             | yum search *pattern*   | urpmq --fuzzy *pkg*        |
|                         |                               | -t pattern *pattern*      |                        |                            |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| Search by file name     | apt-file search *path*        | zypper wp *file*          | yum provides *file*    | urpmf *file*               |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| List installed packages | dpkg -l                       | zypper search -is         | rpm -qa                | rpm -qa                    |    
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| **Configuring access to software repositories**                                                                                           |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| List repositories       | cat /etc/apt/sources.list     | zypper repos              | yum repolist           | urpmq --list-media         |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| Add repository          | (edit /etc/apt/sources.list)  | zypper addrepo            | (add repo to           | urpmi.addmedia *name path* |
|                         |                               | *path name*               | /etc/yum.repos.d/)     |                            |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+
| Remove repository       | (edit /etc/apt/sources.list)  | zypper removerepo *name*  | (remove repo from      | urpmi.removemedia *media*  |
|                         |                               |                           | /etc/yum.repos.d/)     |                            |
+-------------------------+-------------------------------+---------------------------+------------------------+----------------------------+

Slackware and Slackware Based Distributions
+++++++++++++++++++++++++++++++++++++++++++

The table below lists package management utilities found in `Slackware`_ Linux
and other Slackware-based distributions. As stated by Patrick Volkerding on
several occasions, Slackware is unlikely to ever have any advanced (i.e.
dependency-resolving) package management tool, so all installation, upgrade
and removal tasks continue to be performed with *pkgtools*, a set of very simple
scripts that haven't changed much in years. Nevertheless, *slackpkg*, an
advanced package management tool which for years had been relegated to the
unsupported "extra" repository, was finally made part of Slackware Linux 12.2.
It's worth noting that some popular Slackware derivatives, such as
`VectorLinux`_, have standardised on *slapt-get*, another third-party utility
imitating the behaviour of Debian's APT, while `Zenwalk`_ Linux has introduced
its own package management tool called netpkg.

.. _Slackware: http://distrowatch.com/slackware
.. _VectorLinux: http://distrowatch.com/vector
.. _Zenwalk: http://distrowatch.com/zenwalk 

+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| Task                    | pkgtools Slackware     | slackpkg Slackware        | slapt-get Vector               | netpkg Zenwalk             |
+=========================+========================+===========================+================================+============================+
| **Managing software**                                                                                                                      |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| Install new software    | *--*                   | slackpkg install *pkg*    | slapt-get --install *pkg*      | netpkg *pkg*               |
| from package repository |                        |                           |                                |                            |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| Install new software    | installpkg *pkg*       | slackpkg install *pkg*    | slapt-get --install *pkg*      | netpkg *pkg*               |
| from package file       |                        |                           |                                |                            |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| Update existing         | upgradepkg *pkg*       | slackpkg upgrade *pkg*    | slapt-get --install *pkg*      | netpkg *pkg*               |
| software                |                        |                           |                                |                            |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| Remove unwanted         | removepkg *pkg*        | slackpkg remove *pkg*     | slapt-get --remove *pkg*       | netpkg remove *pkg*        |
| software                |                        |                           |                                |                            |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| **Updating the system**                                                                                                                    |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| Update package list     | *--*                   | slackpkg update           | slapt-get --update             | (automatic)                |
|                         |                        |                           |                                |                            |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| Update system           | *--*                   | slackpkg upgrade-all      | slapt-get --upgrade            | netpkg upgrade             |
|                         |                        |                           |                                |                            |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| **Searching for packages**                                                                                                                 |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| Search by package name  | *--*                   | slackpkg search *pkg*     | slapt-get --search *pkg*       | netpkg *pkg* repo          |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| Search by pattern       | *--*                   | slackpkg search *pattern* | slapt-get --search *pattern*   | netpkg list ``|``          | 
|                         |                        |                           |                                | grep *pattern*             |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| Search by file name     | *--*                   | *--*                      | *--*                           | netpkg *file* repo         |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| List installed packages | ls /var/log/packages/  | ls /var/log/packages/     | slapt-get --installed          | netpk list I               |    
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| **Configuring access to software repositories**                                                                                            |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| List repositories       | *--*                   | cat /etc/slackpkg/mirrors | cat /etc/slapt-get/slapt-getrc | netpkg mirror              |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| Add repository          | *--*                   | (edit                     | (edit                          | (edit                      |
|                         |                        | /etc/slackpkg/mirrors)    | /etc/slapt-get/slapt-getrc)    | /etc/netpkg.conf)          |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+
| Remove repository       | *--*                   | (edit                     | (edit                          | (edit                      |
|                         |                        | /etc/slackpkg/mirrors)    | /etc/slapt-get/slapt-getrc)    | /etc/netpkg.conf)          |
+-------------------------+------------------------+---------------------------+--------------------------------+----------------------------+

Independent Linux Distributions
+++++++++++++++++++++++++++++++

In the next group we have a few (mostly) independent distributions that have
been gaining popularity in recent years. `Sabayon`_ Linux, although derived from
Gentoo, has introduced its own command-line package management utility called
*equo*. `Arch`_ Linux's *Pacman* has been around for a long time and it's often
considered one of the fastest package management utilities around. *Conary*,
developed by `rPath`_ and popularised by `Foresight`_ Linux, is a completely new
approach to package management, created by well-known ex-Red Hat engineers
with many years of package management experience. In contrast, *PiSi* by
`Pardus`_ Linux is a relatively new utility, but the distribution itself has been
growing fast in the last couple of years.

.. _Sabayon: http://distrowatch.com/sabayon
.. _Arch: http://distrowatch.com/arch
.. _rPath: http://distrowatch.com/rpath
.. _Foresight: http://distrowatch.com/foresight
.. _Pardus: http://distrowatch.com/pardus

+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| Task                    | equo Sabayon           | pacman Arch              | conary rPath, Foresight    | pisi Pardus               |
+=========================+========================+==========================+============================+===========================+
| **Managing software**                                                                                                                |
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| Install new software    | equo install *pkg*     | pacman -S *pkg*          | conary update *pkg*        | pisi install *pkg*        |
| from package repository |                        |                          |                            |                           |
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| Install new software    | equo install *pkg*     | pacman -U *pkg*          | conary update *pkg*        | pisi install *pkg*        |
| from package file       |                        |                          |                            |                           |
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| Update existing         | equo install *pkg*     | pacman -S *pkg*          | conary update *pkg*        | pisi install *pkg*        |
| software                |                        |                          |                            |                           |
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| Remove unwanted         | equo remove *pkg*      | pacman -R *pkg*          | conary erase *pkg*         | pisi remove *pkg*         |
| software                |                        |                          |                            |                           |
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| **Updating the system**                                                                                                              |
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| Update package list     | equo update            | pacman -Sy               |                            | pisi update-repo          |
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| Update system           | equo world             | pacman -Su               | conary updateall           | pisi upgrade              |
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| **Searching for packages**                                                                                                           |
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| Search by package name  | equo match *pkg*       | pacman -Ss *pkg*         | conary query *pkg*         | pisi search *pkg*         |
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| Search by pattern       | equo search *pattern*  | pacman -Ss *pattern*     | conary query *pkg*         | pisi search *pkg*         | 
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| Search by file name     | equo belongs *file*    | pacman -Qo *file*        | conary query --path *path* | pisi search-file *path*   |
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| List installed packages | equo list              | pacman -Q                | conary query               | pisi list-installed       |    
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| **Configuring access to software repositories**                                                                                      |
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| List repositories       |                        | cat /etc/pacman.conf     |                            | pisi list-repo            |
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| Add repository          |                        | (edit /etc/pacman.conf)  |                            | pisi add-repo *name path* |
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+
| Remove repository       |                        | (edit /etc/pacman.conf)  |                            | pisi remove-repo *name*   |
+-------------------------+------------------------+--------------------------+----------------------------+---------------------------+

Distribution Agnostic Package Management
++++++++++++++++++++++++++++++++++++++++

Besides standard package management utilities that most distributions use as
part of their systems, there are also some distro-agnostic ones that have been
deployed with various levels of success in certain distributions. *Smart*,
originally developed by Conectiva, hasn't been in the news lately, but some
users seem to prefer it over Mandriva's *urpmi* or openSUSE's *zypper* (it also
supports Debian and Slackware-based systems). More recently it is Fedora's
PackageKit that has been gaining momentum as a way to manage packages across
distributions and architectures. Now included in many other distributions,
PackageKit's *pkgcon* command-line utility is effectively a unified front-end to
the native package management tools of Fedora, Ubuntu, openSUSE, Mandriva and
other distributions.

+-------------------------+--------------------------+--------------------------+
| Task                    | smart Mandriva,          | pkgcon Fedora, Ubuntu,   |
|                         | openSUSE                 | openSUSE, Mandriva       |
+=========================+==========================+==========================+
| **Managing software**                                                         |
+-------------------------+--------------------------+--------------------------+
| Install new software    | smart install *pkg*      | pkcon install *pkg*      |
| from package repository |                          |                          |
+-------------------------+--------------------------+--------------------------+
| Install new software    | smart install *pkg*      | pkcon install-file *pkg* |
| from package file       |                          |                          |
+-------------------------+--------------------------+--------------------------+
| Update existing         | smart install *pkg*      | pkcon update *pkg*       |
| software                |                          |                          |
+-------------------------+--------------------------+--------------------------+
| Remove unwanted         | smart remove *pkg*       | pkcon remove *pkg*       |
| software                |                          |                          |
+-------------------------+--------------------------+--------------------------+
| **Updating the system**                                                       | 
+-------------------------+--------------------------+--------------------------+
| Update package list     | smart update             | pkcon refresh            |
+-------------------------+--------------------------+--------------------------+
| Update system           | smart upgrade            | pkcon upgrade            |
+-------------------------+--------------------------+--------------------------+
| **Searching for packages**                                                    |
+-------------------------+--------------------------+--------------------------+
| Search by package name  | smart search *pkg*       | pkcon search name *pkg*  |
+-------------------------+--------------------------+--------------------------+
| Search by pattern       | smart search *pattern*   | pkcon search details     |
|                         |                          | *pattern*                |
+-------------------------+--------------------------+--------------------------+
| Search by file name     | smart query *file*       | pkcon what-provides      |
|                         |                          | *file*                   |
+-------------------------+--------------------------+--------------------------+
| List installed packages | smart query --installed  | *--*                     |
+-------------------------+--------------------------+--------------------------+
| **Configuring access to software repositories**                               |
+-------------------------+--------------------------+--------------------------+
| List repositories       | smart channel --show     | pkcon repo-list          |
+-------------------------+--------------------------+--------------------------+
| Add repository          | smart channel --add      |                          |
|                         | *name path*              |                          |
+-------------------------+--------------------------+--------------------------+
| Remove repository       | smart channel --remove   |                          |
|                         | *name*                   |                          |
+-------------------------+--------------------------+--------------------------+

Source Based Distributions
++++++++++++++++++++++++++

Next, a table for source-based distributions. `Gentoo`_'s Portage is
well-documented and widely used, but other distributions that are designed to
be built from scratch don't often feature in the Linux media, so their package
management systems are not particularly well-known. `Sorcerer`_, which existed
even before Gentoo Linux was conceived, uses Bash scripts to "cast spells" or
download, install and compile packages. Sorcerer was later forked into
`Lunar`_ Linux and `Source Mage`_ GNU/Linux, both of which are included in the
table below. Unfortunately, Sorcerer doesn't offer much in terms of online
documentation so it has been omitted for now.

.. _Gentoo: http://distrowatch.com/gentoo
.. _Sorcerer: http://distrowatch.com/sorcerer
.. _Lunar: http://distrowatch.com/lunar
.. _Source Mage: http://distrowatch.com/sourcemage

+-------------------------+------------------------+---------------------------+--------------------------------+
| Task                    | portage Gentoo         | lunar Lunar               | sorcery Source Mage            |
+=========================+========================+===========================+================================+
| **Managing software**                                                                                         |
+-------------------------+------------------------+---------------------------+--------------------------------+
| Install new software    | emerge *pkg*           | lin *pkg*                 | cast *pkg*                     |
| from package repository |                        |                           |                                |
+-------------------------+------------------------+---------------------------+--------------------------------+
| Install new software    |                        |                           |                                |
| from package file       |                        |                           |                                |
+-------------------------+------------------------+---------------------------+--------------------------------+
| Update existing         | emerge *pkg*           | lin *pkg*                 | cast *pkg*                     |
| software                |                        |                           |                                |
+-------------------------+------------------------+---------------------------+--------------------------------+
| Remove unwanted         | emerge -aC *pkg*       | lrm *pkg*                 | dispel *pkg*                   |
| software                |                        |                           |                                |
+-------------------------+------------------------+---------------------------+--------------------------------+
| **Updating the system**                                                                                       | 
+-------------------------+------------------------+---------------------------+--------------------------------+
| Update package list     | emerge --sync          | lin moonbase              | scribe update                  |
|                         |                        |                           |                                |
+-------------------------+------------------------+---------------------------+--------------------------------+
| Update system           | emerge -NuDa world     | lunar update              | sorcery upgrade                |
|                         |                        |                           |                                |
+-------------------------+------------------------+---------------------------+--------------------------------+
| **Searching for packages**                                                                                    | 
+-------------------------+------------------------+---------------------------+--------------------------------+
| Search by package name  | emerge --search *pkg*  | lvu search *pkg*          | gaze search -name *pkg*        |
+-------------------------+------------------------+---------------------------+--------------------------------+
| Search by pattern       | emerge --search        | lvu search *pattern*      | gaze search *pattern*          |
|                         | *pattern*              |                           |                                |
+-------------------------+------------------------+---------------------------+--------------------------------+
| Search by file name     | equery belongs *pkg*   |                           | gaze from *file*               |
+-------------------------+------------------------+---------------------------+--------------------------------+
| List installed packages | qlist -I               | lvu installed             | gaze installed                 |
+-------------------------+------------------------+---------------------------+--------------------------------+
| **Configuring access to software repositories**                                                               |
+-------------------------+------------------------+---------------------------+--------------------------------+
| List repositories       | layman -L              | *--*                      | scribe index                   |
+-------------------------+------------------------+---------------------------+--------------------------------+
| Add repository          | layman -a *repo*       | *--*                      | scribe add *repo*              |
+-------------------------+------------------------+---------------------------+--------------------------------+
| Remove repository       | layman -d *repo*       | *--*                      | scribe remove *repo*           |
+-------------------------+------------------------+---------------------------+--------------------------------+

FreeBSD
+++++++

Finally, a table for FreeBSD, a popular operating system offering both binary
and source package management.

+-------------------------+------------------------+----------------------------------------------------+
| Task                    | packages FreeBSD       | ports FreeBSD                                      |    
+=========================+========================+====================================================+
| **Managing software**                                                                                 | 
+-------------------------+------------------------+----------------------------------------------------+
| Install new software    | pkg_add -r *package*   | cd port_dir && make                                |
| from package repository |                        | && make install                                    |
+-------------------------+------------------------+----------------------------------------------------+
| Install new software    | pkg_add                | *--*                                               |
| from package file       | *path_to_package*      |                                                    |
+-------------------------+------------------------+----------------------------------------------------+
| Update existing         | pkg_add                | portupgrade -R *pkg*                               |
| software                | *path_to_package*      |                                                    |
+-------------------------+------------------------+----------------------------------------------------+
| Remove unwanted         | pkg_delete *pkg*       | pkg_delete *pkg*                                   |
| software                |                        |                                                    |
+-------------------------+------------------------+----------------------------------------------------+
| **Updating the system** | freebsd-update         | portsnap fecth install                             | 
|                         | fetch install          |                                                    | 
+-------------------------+------------------------+----------------------------------------------------+
| Update package list     |                        | | csup -L 2 -h cvsup.FreeBSD.org *path_to_supfile* |
|                         |                        | | portsnap update                                  |
+-------------------------+------------------------+----------------------------------------------------+
| Update system           |                        | | portupgrade -a                                   |
|                         |                        | | portmanager -u                                   |
|                         |                        | | portmaster -a                                    |
+-------------------------+------------------------+----------------------------------------------------+
| **Searching for packages**                                                                            | 
+-------------------------+------------------------+----------------------------------------------------+
| Search by package name  |                        | cd /usr/ports && make search *pkg*                 |
+-------------------------+------------------------+----------------------------------------------------+
| Search by pattern       |                        | cd /usr/ports && make search *pattern*             |
|                         |                        |                                                    |
+-------------------------+------------------------+----------------------------------------------------+
| Search by file name     |                        |                                                    |
+-------------------------+------------------------+----------------------------------------------------+
| List installed packages | pkg_info               | pkg_info                                           |
+-------------------------+------------------------+----------------------------------------------------+
| **Configuring access to software repositories**                                                       | 
+-------------------------+------------------------+----------------------------------------------------+
| List repositories       | *--*                   | *--*                                               |
+-------------------------+------------------------+----------------------------------------------------+
| Add repository          | *--*                   | *--*                                               |
+-------------------------+------------------------+----------------------------------------------------+
| Remove repository       | *--*                   | *--*                                               |
+-------------------------+------------------------+----------------------------------------------------+

-------

Copyright © 2009 DistroWatch.com.

*Verbatim copying and distribution of this entire article is permitted in any
medium, provided this copyright notice is preserved.*


