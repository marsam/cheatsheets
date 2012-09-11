
===============================================================================
Package Management Cheatsheet
===============================================================================
A package management reference card for Linux distributions and FreeBSD
===============================================================================

.. :Authors: DistroWatch.com (http://distrowatch.com/packages.php); Mario Rodas (pdf version)

Introduction
-------------------------------------------------------------------------------
Package management is probably the most distinctive feature of any Linux
distribution. While the current trend among most of the major projects is to
offer some sort of a clickable interface where users can select a package and
install it with a mouse click (e.g. Debian's Synaptic or Mandriva's Drakrpm),
these types of programs are generally just graphical front-ends to the
low-level utilities that manage the tasks associated with installing packages
on a Linux system. And even though many desktop Linux users feel much more
comfortable installing packages through these intuitive graphical tools, there
is no denying that command-line package management offers two excellent
features not available in any graphical package management utility: power and
speed.

One problem that many distro-hoppers and operating system enthusiasts encounter
is having to master (or relearn) a set of package management commands each time
they switch from one distribution group to another.  Additionally, the package
management tools tend to evolve, with new features and even new commands added
to every new version. This is why we created this package management cheatsheet
- an easy reference card covering most frequently used package management tasks
in Linux distributions and FreeBSD.  As always, we welcome corrections, updates
and suggestions - if you spot any error or wish to have another package
management utility added to this page, feel free to contact us (email address
at the bottom of this page).

.. Package Management Cheatsheet

Cheatsheet
-------------------------------------------------------------------------------

Main distributions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The first table lists package management tasks in the four most popular
distribution groups - Debian_ (including Ubuntu_, Linux Mint_, KNOPPIX_, sidux_
and other Debian derivatives), openSUSE_, Fedora_ (including `Red Hat`_
Enterprise Linux, CentOS_, Scientific_ Linux and other Fedora-based
distributions), and Mandriva_ Linux.

======================= =============================== =============================== ======================= ===========================
Task			|apt|				|zypp|				|yum|			|urpmi|
======================= =============================== =============================== ======================= ===========================
**Managing software**
-------------------------------------------------------------------------------------------------------------------------------------------
|install_from_repo|	apt-get install *pkg*		zypper install *pkg*		yum install *pkg*	urpmi *pkg*
|install_from_pkg|	dpkg -i *pkg*			zypper install *pkg*		yum localinstall *pkg*	urpmi *pkg*
|update_pkg|		apt-get install *pkg*		zypper update -t package *pkg*	yum update *pkg*	urpmi *pkg*
|remove_pkg|		apt-get remove *pkg*		zypper remove *pkg*		yum erase *pkg*		urpme *pkg*
**Updating the system**
-------------------------------------------------------------------------------------------------------------------------------------------
|update_pkg_list|	apt-get update			zypper refresh			yum check-update	urpmi.update -a
			aptitude update
|update_system|		| apt-get upgrade		zypper update			yum update		urpmi --auto-select
			| aptitude safe-upgrade
**Searching for packages**
-------------------------------------------------------------------------------------------------------------------------------------------
|search_name|		apt-cache search *pkg*		zypper search *pkg*		yum list *pkg*		urpmq *pkg*
|search_pattern|	apt-cache search *pattern*	zypper search			yum search *pattern*	urpmq --fuzzy *pkg*
							-t pattern *pattern*
|search_file|		apt-file search *path*		zypper wp *file*		yum provides *file*	urpmf *file*
|list_installed|	dpkg -l				zypper search -is		rpm -qa			rpm -qa
**Configuring access to software repositories**
-------------------------------------------------------------------------------------------------------------------------------------------
|list_repos|		cat /etc/apt/sources.list	zypper repos			yum repolist		urpmq --list-media
|add_repo|		(edit /etc/apt/sources.list)	zypper addrepo	*path name*	(add repo to		urpmi.addmedia *name path*
											/etc/yum.repos.d/)
|remove_repo|		(edit /etc/apt/sources.list)	zypper removerepo *name*	(remove repo from	urpmi.removemedia *media*
											/etc/yum.repos.d/)
======================= =============================== =============================== ======================= ===========================


Slackware and Slackware Based Distributions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The table below lists package management utilities found in Slackware_ Linux
and other Slackware-based distributions. As stated by Patrick Volkerding on
several occasions, Slackware is unlikely to ever have any advanced (i.e.
dependency-resolving) package management tool, so all installation, upgrade and
removal tasks continue to be performed with *pkgtools*, a set of very simple
scripts that haven't changed much in years. Nevertheless, *slackpkg*, an
advanced package management tool which for years had been relegated to the
unsupported "extra" repository, was finally made part of Slackware Linux 12.2.
It's worth noting that some popular Slackware derivatives, such as
VectorLinux_, have standardised on *slapt-get*, another third-party utility
imitating the behaviour of Debian's APT, while Zenwalk_ Linux has introduced
its own package management tool called netpkg.

=============================== ======================= =============================== ======================================= ==============================
Task				|pkgtools|		|slackpkg|			|slapt-get|				|netpkg|
=============================== ======================= =============================== ======================================= ==============================
**Managing software**
--------------------------------------------------------------------------------------------------------------------------------------------------------------
|install_from_repo|		|--|			slackpkg install *pkg*		slapt-get --install *pkg*		netpkg *pkg*
|install_from_pkg|		installpkg *pkg*	slackpkg install *pkg*		slapt-get --install *pkg*		netpkg *pkg*
|update_pkg|			upgradepkg *pkg*	slackpkg upgrade *pkg*		slapt-get --install *pkg*		netpkg *pkg*
|remove_pkg|			removepkg *pkg*		slackpkg remove *pkg*		slapt-get --remove *pkg*		netpkg remove *pkg*
**Updating the system**
--------------------------------------------------------------------------------------------------------------------------------------------------------------
|update_pkg_list|		|--|			slackpkg update			slapt-get --update			(automatic)
|update_system|			|--|			slackpkg upgrade-all		slapt-get --upgrade			netpkg upgrade
**Searching for packages**
--------------------------------------------------------------------------------------------------------------------------------------------------------------
|search_name|			|--|			slackpkg search *pkg*		slapt-get --search *pkg*		netpkg *pkg* repo
|search_pattern|		|--|			slackpkg search *pattern*	slapt-get --search *pattern*		netpkg list | grep *pattern*
|search_file|			|--|			|--|				|--|					netpkg *file* repo
|list_installed|		ls /var/log/packages/	ls /var/log/packages/		slapt-get --installed			netpk list I
**Configuring access to software repositories**
--------------------------------------------------------------------------------------------------------------------------------------------------------------
|list_repos|			|--|			cat /etc/slackpkg/mirrors	cat /etc/slapt-get/slapt-getrc		netpkg mirror
|add_repo|			|--|			(edit /etc/slackpkg/mirrors)	(edit /etc/slapt-get/slapt-getrc)	(edit /etc/netpkg.conf)
|remove_repo|			|--|			(edit /etc/slackpkg/mirrors)	(edit /etc/slapt-get/slapt-getrc)	(edit /etc/netpkg.conf)
=============================== ======================= =============================== ======================================= ==============================


Independent Linux Distributions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In the next group we have a few (mostly) independent distributions that have
been gaining popularity in recent years. `Sabayon`_ Linux, although derived
from Gentoo, has introduced its own command-line package management utility
called *equo*. `Arch`_ Linux's *Pacman* has been around for a long time and
it's often considered one of the fastest package management utilities around.
*Conary*, developed by `rPath`_ and popularised by `Foresight`_ Linux, is a
completely new approach to package management, created by well-known ex-Red Hat
engineers with many years of package management experience. In contrast, *PiSi*
by `Pardus`_ Linux is a relatively new utility, but the distribution itself has
been growing fast in the last couple of years.

======================= ======================= ======================= =============================== ==========================
Task			|equo|			|pacman|		|conary|			|pisi|
======================= ======================= ======================= =============================== ==========================
**Managing software**
----------------------------------------------------------------------------------------------------------------------------------
|install_from_repo|	equo install *pkg*	pacman -S *pkg*		conary update *pkg*		pisi install *pkg*
|install_from_pkg|	equo install *pkg*	pacman -U *pkg*		conary update *pkg*		pisi install *pkg*
|update_pkg|		equo install *pkg*	pacman -S *pkg*		conary update *pkg*		pisi install *pkg*
|remove_pkg|		equo remove *pkg*	pacman -R *pkg*		conary erase *pkg*		pisi remove *pkg*
**Updating the system**
----------------------------------------------------------------------------------------------------------------------------------
|update_pkg_list|	equo update		pacman -Sy		|--|				pisi update-repo
|update_system|		equo world		pacman -Su		conary updateall		pisi upgrade
**Searching for packages**
----------------------------------------------------------------------------------------------------------------------------------
|search_name|		equo match *pkg*	pacman -Ss *pkg*	conary query *pkg*		pisi search *pkg*
|search_pattern|	equo search *pattern*	pacman -Ss *pattern*	conary query *pkg*		pisi search *pkg*
|search_file|		equo belongs *file*	pacman -Qo *file*	conary query --path *path*	pisi search-file *path*
|list_installed|	equo list		pacman -Q		conary query			pisi list-installed
**Configuring access to software repositories**
----------------------------------------------------------------------------------------------------------------------------------
|list_repos|		|--|			cat /etc/pacman.conf	|--|				pisi list-repo
|add_repo|		|--|			(edit /etc/pacman.conf)	|--|				pisi add-repo *name path*
|remove_repo|		|--|			(edit /etc/pacman.conf)	|--|				pisi remove-repo *name*
======================= ======================= ======================= =============================== ==========================


Distribution Agnostic Package Management
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Besides standard package management utilities that most distributions use as
part of their systems, there are also some distro-agnostic ones that have been
deployed with various levels of success in certain distributions. *Smart*,
originally developed by Conectiva, hasn't been in the news lately, but some
users seem to prefer it over Mandriva's *urpmi* or openSUSE's *zypper* (it also
supports Debian and Slackware-based systems). More recently it is Fedora's
PackageKit that has been gaining momentum as a way to manage packages across
distributions and architectures. Now included in many other distributions,
PackageKit's *pkgcon* command-line utility is effectively a unified front-end
to the native package management tools of Fedora, Ubuntu, openSUSE, Mandriva
and other distributions.

======================= ======================================= ==================================
Task			|smart|					|pkgcon|
======================= ======================================= ==================================
**Managing software**
--------------------------------------------------------------------------------------------------
|install_from_repo|	smart install *pkg*			pkcon install *pkg*
|install_from_pkg|	smart install *pkg*			pkcon install-file *pkg*
|update_pkg|		smart install *pkg*			pkcon update *pkg*
|remove_pkg|		smart remove *pkg*			pkcon remove *pkg*
**Updating the system**
--------------------------------------------------------------------------------------------------
|update_pkg_list|	smart update				pkcon refresh
|update_system|		smart upgrade				pkcon upgrade
**Searching for packages**
--------------------------------------------------------------------------------------------------
|search_name|		smart search *pkg*			pkcon search name *pkg*
|search_pattern|	smart search *pattern*			pkcon search details *pattern*
|search_file|		smart query *file*  			pkcon what-provides *file*
|list_installed|	smart query --installed			|--|
**Configuring access to software repositories**
--------------------------------------------------------------------------------------------------
|list_repos|		smart channel --show			pkcon repo-list
|add_repo|		smart channel --add *name path*		|--|
|remove_repo|		smart channel --remove *name*		|--|
======================= ======================================= ==================================

Source Based Distributions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Next, a table for source-based distributions. Gentoo_'s Portage is
well-documented and widely used, but other distributions that are designed to
be built from scratch don't often feature in the Linux media, so their package
management systems are not particularly well-known. Sorcerer_, which existed
even before Gentoo Linux was conceived, uses Bash scripts to "cast spells" or
download, install and compile packages. Sorcerer was later forked into Lunar_
Linux and `Source Mage`_ GNU/Linux, both of which are included in the table
below. Unfortunately, Sorcerer doesn't offer much in terms of online
documentation so it has been omitted for now.

=============================== =============================== ======================= ===========================
Task				|portage|			|lunar|			|sorcery|
=============================== =============================== ======================= ===========================
**Managing software**
-------------------------------------------------------------------------------------------------------------------
|install_from_repo|		emerge *pkg*			lin *pkg*		cast *pkg*
|install_from_pkg|		|--|				|--|			|--|
|update_pkg|			emerge *pkg*			lin *pkg*		cast *pkg*
|remove_pkg|			emerge -aC *pkg*		lrm *pkg*		dispel *pkg*
**Updating the system**
-------------------------------------------------------------------------------------------------------------------
|update_pkg_list|		emerge --sync			lin moonbase		scribe update
|update_system|			emerge -NuDa world		lunar update		sorcery upgrade
**Searching for packages**
-------------------------------------------------------------------------------------------------------------------
|search_name|			emerge --search *pkg*		lvu search *pkg*	gaze search -name *pkg*
|search_pattern|		emerge --search *pattern*	lvu search *pattern*	gaze search *pattern*
|search_file|			equery belongs *pkg*		|--|			gaze from *file*
|list_installed|		qlist -I			lvu installed		gaze installed
**Configuring access to software repositories**
-------------------------------------------------------------------------------------------------------------------
|list_repos|			layman -L			|--|			scribe index
|add_repo|			layman -a *repo*		|--|			scribe add *repo*
|remove_repo|			layman -d *repo*		|--|			scribe remove *repo*
=============================== =============================== ======================= ===========================

FreeBSD
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Finally, a table for FreeBSD, a popular operating system offering both binary
and source package management.

=============================== =============================== ======================================================
Task				|packages|			|ports|
=============================== =============================== ======================================================
**Managing software**
----------------------------------------------------------------------------------------------------------------------
|install_from_repo|		pkg_add -r *package*		cd port_dir && make && make install
|install_from_pkg|		pkg_add *path_to_package*	|--|
|update_pkg|			pkg_add *path_to_package*	portupgrade -R *pkg*
|remove_pkg|			pkg_delete *pkg*		pkg_delete *pkg*
**Updating the system**		| freebsd-update		portsnap fecth install
				| fetch install
|update_pkg_list|		|--|				| csup -L 2 -h cvsup.FreeBSD.org *path_to_supfile*
								| portsnap update
|update_system|			|--|				| portupgrade -a
				|--|				| portmanager -u
				|--|				| portmaster -a
**Searching for packages**
----------------------------------------------------------------------------------------------------------------------
|search_name|			|--|				cd /usr/ports && make search *pkg*
|search_pattern|		|--|				cd /usr/ports && make search *pattern*
|search_file|			|--|				|--|
|list_installed|		pkg_info			pkg_info
**Configuring access to software repositories**
----------------------------------------------------------------------------------------------------------------------
|list_repos|			|--|				|--|
|add_repo|			|--|				|--|
|remove_repo|			|--|				|--|
=============================== =============================== ======================================================

-------

Copyright © 2009 DistroWatch.com.

*Verbatim copying and distribution of this entire article is permitted in any
medium, provided this copyright notice is preserved.*

.. Package Managers: {{{

.. |apt|            replace:: apt (deb) Debian_, Ubuntu_, Mint_
.. |zypp|           replace:: zypp (rpm) openSUSE_
.. |yum|            replace:: yum (rpm) Fedora_
.. |urpmi|          replace:: urpmi (rpm) Mandriva_
.. |pkgtools|       replace:: pkgtools Slackware_
.. |slackpkg|       replace:: slackpkg Slackware_
.. |slapt-get|      replace:: slapt-get VectorLinux_
.. |netpkg|         replace:: netpkg Zenwalk_
.. |equo|           replace:: equo Sabayon_
.. |pacman|         replace:: pacman Arch_
.. |conary|         replace:: conary rPath_, Foresight_
.. |pisi|           replace:: pisi Pardus_
.. |smart|          replace:: smart Mandriva_, openSUSE_
.. |pkgcon|         replace:: pkgcon Fedora_, Ubuntu_, openSUSE_, Mandriva_
.. |portage|        replace:: portage Gentoo_
.. |lunar|          replace:: lunar Lunar_
.. |sorcery|        replace:: sorcery `Source Mage`_
.. |packages|       replace:: packages FreeBSD_
.. |ports|          replace:: ports FreeBSD_

.. }}}

.. Tasks: {{{

.. |install_from_repo|  replace:: Install new software from package repository
.. |install_from_pkg|   replace:: Install new software from package file
.. |update_pkg|         replace:: Update existing software
.. |remove_pkg|         replace:: Remove unwanted software
.. |update_pkg_list|    replace:: Update package list
.. |update_system|      replace:: Update system
.. |search_name|        replace:: Search by package name
.. |search_pattern|     replace:: Search by pattern
.. |search_file|        replace:: Search by file name
.. |list_installed|     replace:: List installed packages
.. |list_repos|         replace:: List repositories
.. |add_repo|           replace:: Add repository
.. |remove_repo|        replace:: Remove repository

.. }}}

.. Linux Distributions: {{{
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
.. _Slackware: http://distrowatch.com/slackware
.. _VectorLinux: http://distrowatch.com/vector
.. _Zenwalk: http://distrowatch.com/zenwalk
.. _Sabayon: http://distrowatch.com/sabayon
.. _Arch: http://distrowatch.com/arch
.. _rPath: http://distrowatch.com/rpath
.. _Foresight: http://distrowatch.com/foresight
.. _Pardus: http://distrowatch.com/pardus
.. _Gentoo: http://distrowatch.com/gentoo
.. _Sorcerer: http://distrowatch.com/sorcerer
.. _Lunar: http://distrowatch.com/lunar
.. _Source Mage: http://distrowatch.com/sourcemage
.. }}}

.. Symbols {{{
.. |--| unicode:: U+2013

.. }}}

.. vim:ft=rst:tw=79:cuc:fdm=marker:
