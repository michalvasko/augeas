GNULIB= ../gnulib/lib/libgnu.la
GNULIB_CFLAGS= -I $(top_srcdir)/gnulib/lib

AM_CFLAGS = $(AUGEAS_CFLAGS) $(WARN_CFLAGS) $(GNULIB_CFLAGS) \
	 $(LIBXML_CFLAGS) -I $(top_builddir)/src

VALGRIND=libtool --mode=execute valgrind --quiet --leak-check=full
valgrind:
	$(MAKE) $(MAKEFLAGS) check \
	  VALGRIND="$(VALGRIND)" \
	  AUGPARSE=$(abs_top_builddir)/src/augparse \
	  AUGTOOL=$(abs_top_builddir)/src/augtool
	$(VALGRIND) ./fatest

valgrind-leak: leak
	$(TESTS_ENVIRONMENT) $(VALGRIND) ./leak

lens_tests =			\
  lens-sudoers.sh		\
  lens-access.sh		\
  lens-activemq_conf.sh		\
  lens-activemq_xml.sh		\
  lens-afs_cellalias.sh			\
  lens-aliases.sh		\
  lens-anaconda.sh		\
  lens-anacron.sh		\
  lens-approx.sh		\
  lens-apt_update_manager.sh		\
  lens-aptcacherngsecurity.sh		\
  lens-aptpreferences.sh	\
  lens-aptconf.sh	\
  lens-aptsources.sh		\
  lens-authinfo2.sh	\
  lens-authorized_keys.sh	\
  lens-authselectpam.sh \
  lens-automaster.sh	\
  lens-automounter.sh	\
  lens-avahi.sh	\
  lens-backuppchosts.sh		\
  lens-bbhosts.sh		\
  lens-bootconf.sh		\
  lens-build.sh		\
  lens-cachefilesd.sh		\
  lens-carbon.sh	\
  lens-cgconfig.sh		\
  lens-cgrules.sh  		\
  lens-channels.sh  		\
  lens-chrony.sh  		\
  lens-ceph.sh  		\
  lens-clamav.sh        \
  lens-cmdline.sh	\
  lens-cobblersettings.sh	\
  lens-cobblermodules.sh	\
  lens-collectd.sh	\
  lens-cpanel.sh	\
  lens-cron.sh			\
  lens-cron_user.sh			\
  lens-crypttab.sh		\
  lens-csv.sh		\
  lens-cyrus_imapd.sh		\
  lens-cups.sh		\
  lens-darkice.sh		\
  lens-debctrl.sh		\
  lens-desktop.sh	\
  lens-devfsrules.sh \
  lens-device_map.sh    \
  lens-dhclient.sh		\
  lens-dhcpd.sh		\
  lens-dns_zone.sh		\
  lens-dnsmasq.sh		\
  lens-dovecot.sh		\
  lens-dpkg.sh			\
  lens-dput.sh			\
  lens-erlang.sh		\
  lens-ethers.sh		\
  lens-exports.sh		\
  lens-fai_diskconfig.sh	\
  lens-fail2ban.sh	\
  lens-fonts.sh	\
  lens-fstab.sh			\
  lens-fuse.sh			\
  lens-gdm.sh			\
  lens-getcap.sh		\
  lens-group.sh			\
  lens-grubenv.sh			\
  lens-gshadow.sh			\
  lens-gtkbookmarks.sh			\
  lens-json.sh          \
  lens-hostname.sh			\
  lens-hosts.sh			\
  lens-hosts_access.sh			\
  lens-host_conf.sh			\
  lens-htpasswd.sh         \
  lens-httpd.sh         \
  lens-inetd.sh         \
  lens-inifile.sh		\
  lens-inittab.sh		\
  lens-inputrc.sh		\
  lens-interfaces.sh		\
  lens-iptables.sh		\
  lens-iproute2.sh		\
  lens-iscsid.sh		\
  lens-jettyrealm.sh		\
  lens-jmxaccess.sh		\
  lens-jmxpassword.sh		\
  lens-kdump.sh			\
  lens-keepalived.sh	\
  lens-known_hosts.sh	\
  lens-koji.sh			\
  lens-krb5.sh			\
  lens-jaas.sh          \
  lens-ldap.sh			\
  lens-ldif.sh			\
  lens-ldso.sh			\
  lens-lightdm.sh		\
  lens-limits.sh		\
  lens-login_defs.sh 	\
  lens-logrotate.sh		\
  lens-logwatch.sh		\
  lens-lokkit.sh		\
  lens-lvm.sh			\
  lens-mailscanner.sh   \
  lens-mailscanner_rules.sh	\
  lens-masterpasswd.sh	\
  lens-mcollective.sh 	\
  lens-mdadm_conf.sh	\
  lens-memcached.sh		\
  lens-mke2fs.sh		\
  lens-modprobe.sh		\
  lens-modules.sh		\
  lens-modules_conf.sh	\
  lens-mongodbserver.sh		\
  lens-monit.sh			\
  lens-multipath.sh     \
  lens-mysql.sh			\
  lens-nagioscfg.sh     \
  lens-nagiosobjects.sh     \
  lens-netmasks.sh     \
  lens-networkmanager.sh     \
  lens-networks.sh     \
  lens-nginx.sh     \
  lens-ntp.sh			\
  lens-ntpd.sh			\
  lens-nrpe.sh          \
  lens-nsswitch.sh		\
  lens-nslcd.sh			\
  lens-odbc.sh          \
  lens-opendkim.sh          \
  lens-openshift_config.sh	\
  lens-openshift_http.sh	\
  lens-openshift_quickstarts.sh	\
  lens-openvpn.sh		\
  lens-oz.sh		\
  lens-pagekite.sh		\
  lens-pam.sh			\
  lens-pamconf.sh		\
  lens-passwd.sh		\
  lens-pbuilder.sh		\
  lens-pg_hba.sh		\
  lens-pgbouncer.sh     \
  lens-php.sh			\
  lens-phpvars.sh		\
  lens-postfix_access.sh \
  lens-postfix_main.sh		\
  lens-postfix_master.sh	\
  lens-postfix_passwordmap.sh \
  lens-postfix_sasl_smtpd.sh \
  lens-postfix_transport.sh	\
  lens-postfix_virtual.sh	\
  lens-postgresql.sh \
  lens-properties.sh    \
  lens-protocols.sh    \
  lens-puppet.sh		\
  lens-puppet_auth.sh		\
  lens-puppetfile.sh		\
  lens-puppetfileserver.sh		\
  lens-pylonspaste.sh   \
  lens-pythonpaste.sh	\
  lens-qpid.sh		\
  lens-quote.sh		\
  lens-rabbitmq.sh		\
  lens-radicale.sh		\
  lens-rancid.sh		\
  lens-redis.sh		\
  lens-reprepro_uploaders.sh		\
  lens-resolv.sh		\
  lens-rhsm.sh			\
  lens-rmt.sh			\
  lens-rsyncd.sh		\
  lens-rsyslog.sh		\
  lens-rtadvd.sh		\
  lens-rx.sh			\
  lens-samba.sh			\
  lens-securetty.sh     \
  lens-semanage.sh		\
  lens-services.sh		\
  lens-shadow.sh		\
  lens-shells.sh		\
  lens-shellvars.sh		\
  lens-shellvars_list.sh	\
  lens-simplelines.sh	\
  lens-simplevars.sh	\
  lens-sip_conf.sh	    \
  lens-slapd.sh			\
  lens-smbusers.sh			\
  lens-solaris_system.sh		\
  lens-soma.sh			\
  lens-spacevars.sh		\
  lens-splunk.sh		\
  lens-squid.sh			\
  lens-ssh.sh			\
  lens-sshd.sh			\
  lens-sssd.sh			\
  lens-star.sh          \
  lens-strongswan.sh \
  lens-stunnel.sh			\
  lens-subversion.sh		\
  lens-sysconfig.sh		\
  lens-sysconfig_route.sh		\
  lens-syslog.sh		\
  lens-sysctl.sh		\
  lens-systemd.sh		\
  lens-termcap.sh		\
  lens-thttpd.sh		\
  lens-tinc.sh		\
  lens-tmpfiles.sh		\
  lens-trapperkeeper.sh		\
  lens-toml.sh		\
  lens-tuned.sh			\
  lens-up2date.sh		\
  lens-updatedb.sh		\
  lens-util.sh		\
  lens-vfstab.sh		\
  lens-vmware_config.sh		\
  lens-vsftpd.sh		\
  lens-webmin.sh		\
  lens-wine.sh			\
  lens-xinetd.sh		\
  lens-xml.sh			\
  lens-xorg.sh			\
  lens-xymon.sh			\
  lens-xymon_alerting.sh \
  lens-grub.sh			\
  lens-schroot.sh			\
  lens-xendconfsxp.sh	\
  lens-yaml.sh	\
  lens-yum.sh

ME = tests/Makefile.am

# Ensure that the above list stays up to date:
# Construct two lists: list of lens-*.sh from lens_tests = ... above,
# and the list of ../lenses/tests/test_*.aug names.
# If they're not the same, print the new or removed names and fail.
check: check-lens-tests
.PHONY: check-lens-tests
_v = lens_tests
check-lens-tests:
	@u=$$({ sed -n '/^$(_v) =[	 ]*\\$$/,/[^\]$$/p'		\
		$(srcdir)/Makefile.am					\
	    | sed 's/^  *//;/^\$$.*/d;/^$(_v) =/d'			\
	    | sed 's,\.sh.*\\,.sh,';					\
	  ls -1 $(srcdir)/../lenses/tests/test_*.aug			\
	    | sed 's,.*/test_\([^./]*\)\.aug$$,lens-\1.sh,';		\
	} | LC_ALL=C sort | uniq -u);					\
	test "x$$u" = x && :						\
	  || { printf '%s\n' "$$u" >&2;					\
	       echo '$(ME): new test(s)?  update lens_tests' >&2; exit 1; }

DISTCLEANFILES = $(lens_tests)
$(lens_tests): lens-test-1
	rm -f $@
	$(LN_S) $< $@

check_SCRIPTS = \
  test-interpreter.sh \
  $(lens_tests) \
  test-get.sh test-augtool.sh \
  test-put-symlink.sh test-put-symlink-augnew.sh \
  test-put-symlink-augsave.sh test-put-symlink-augtemp.sh \
  test-put-mount.sh test-put-mount-augnew.sh test-put-mount-augsave.sh \
  test-save-empty.sh test-bug-1.sh test-idempotent.sh test-preserve.sh \
  test-events-saved.sh test-save-mode.sh test-unlink-error.sh \
  test-augtool-empty-line.sh test-augtool-modify-root.sh \
  test-span-rec-lens.sh test-nonwritable.sh test-augmatch.sh \
  test-function-modified.sh

EXTRA_DIST = \
  test-augtool root lens-test-1 \
  $(check_SCRIPTS) $(wildcard modules/*.aug) xpath.tests run.tests

noinst_SCRIPTS = $(check_SCRIPTS)

noinst_PROGRAMS = leak

check_PROGRAMS = fatest test-xpath test-load test-perf test-save test-api test-run

TESTS_ENVIRONMENT = \
  PATH='$(abs_top_builddir)/src$(PATH_SEPARATOR)'"$$PATH" \
  abs_top_builddir='$(abs_top_builddir)' \
  abs_top_srcdir='$(abs_top_srcdir)' \
  LANG=en_US

TESTS = $(check_SCRIPTS) $(check_PROGRAMS)

INCLUDES = -I$(top_srcdir)/src

fatest_SOURCES = fatest.c cutest.c cutest.h $(top_srcdir)/src/memory.c $(top_srcdir)/src/memory.h
fatest_LDADD = $(top_builddir)/src/libfa.la $(LIBXML_LIBS) $(GNULIB)

test_xpath_SOURCES = test-xpath.c cutest.c cutest.h $(top_srcdir)/src/memory.c
test_xpath_LDADD = $(top_builddir)/src/libaugeas.la $(LIBXML_LIBS) $(GNULIB)

test_load_SOURCES = test-load.c cutest.c cutest.h $(top_srcdir)/src/memory.c $(top_srcdir)/src/memory.h
test_load_LDADD = $(top_builddir)/src/libaugeas.la $(LIBXML_LIBS) $(GNULIB)

test_save_SOURCES = test-save.c cutest.c cutest.h $(top_srcdir)/src/memory.c $(top_srcdir)/src/memory.h
test_save_LDADD = $(top_builddir)/src/libaugeas.la $(LIBXML_LIBS) $(GNULIB)

test_api_SOURCES = test-api.c cutest.c cutest.h $(top_srcdir)/src/memory.c $(top_srcdir)/src/memory.h
test_api_LDADD = $(top_builddir)/src/libaugeas.la $(LIBXML_LIBS) $(GNULIB)

test_run_SOURCES = test-run.c cutest.c cutest.h $(top_srcdir)/src/memory.c $(top_srcdir)/src/memory.h
test_run_LDADD = $(top_builddir)/src/libaugeas.la $(LIBXML_LIBS) $(GNULIB)

test_perf_SOURCES = test-perf.c cutest.c cutest.h $(top_srcdir)/src/memory.c $(top_srcdir)/src/memory.h
test_perf_LDADD = $(top_builddir)/src/libaugeas.la $(LIBXML_LIBS) $(GNULIB)

leak_SOURCES = leak.c
leak_LDADD =  $(top_builddir)/src/libaugeas.la $(LIBXML_LIBS) $(GNULIB)

FAILMALLOC_START ?= 1
FAILMALLOC_REP   ?= 20
FAILMALLOC_PROG ?= ./fatest

include $(top_srcdir)/Makefile.inc
