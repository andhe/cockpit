LINGUAS =

translations_json = $(addprefix lang/,$(addsuffix .json,$(LINGUAS)))

cockpit_js_PARTS = \
	pkg/shell/polyfills.js \
	pkg/shell/channel.js \
	pkg/shell/dbus.js \
	pkg/shell/rest.js \
	pkg/shell/spawn.js \
	pkg/shell/debug.js \
	pkg/shell/controls.js \
	pkg/shell/cockpit-util.js \
	pkg/shell/cockpit-i18n.js \
	pkg/shell/cockpit-main.js \
	pkg/shell/cockpit-plot.js \
	pkg/shell/cockpit-about.js \
	pkg/shell/cockpit-language.js \
	pkg/shell/cockpit-dashboard.js \
	pkg/shell/cockpit-setup.js \
	pkg/shell/cockpit-server.js \
	pkg/shell/cockpit-cpu-status.js \
	pkg/shell/cockpit-memory-status.js \
	pkg/shell/cockpit-system-information.js \
	pkg/shell/cockpit-networking.js \
	pkg/shell/cockpit-storage.js \
	pkg/shell/cockpit-realms.js \
	pkg/shell/cockpit-shutdown.js \
	pkg/shell/cockpit-services.js \
	pkg/shell/cockpit-journal.js \
	pkg/shell/cockpit-journal-renderer.js \
	pkg/shell/cockpit-terminal.js \
	pkg/shell/cockpit-accounts.js \
	pkg/shell/cockpit-docker.js \
	pkg/shell/cockpit-internal.js \
	pkg/shell/cockpit-init.js \
	$(NULL)

cockpit_js_FILES = cockpit.js
cockpit.js: $(cockpit_js_PARTS)
	$(AM_V_GEN) JSL=$(JSL) $(JSLINT) $^
	$(AM_V_GEN) $(MINIFY) $^ >$@.tmp && mv $@.tmp $@

shelldir = $(pkgdatadir)/shell
nodist_shell_DATA = \
	$(cockpit_js_FILES) \
	$(NULL)
shell_DATA = \
	pkg/shell/cockpit.css \
	pkg/shell/shell.html \
	pkg/shell/release/manifest.json \
	$(NULL)

shelllangdir = $(pkgdatadir)/shell/lang
shelllang_DATA = \
	$(translations_json) \
	$(NULL)

shellimagesdir = $(pkgdatadir)/shell/images
shellimages_DATA = \
	pkg/shell/images/bg-login.jpg \
	pkg/shell/images/category-containers.png \
	pkg/shell/images/category-journal.png \
	pkg/shell/images/category-networking.png \
	pkg/shell/images/category-services.png \
	pkg/shell/images/category-shutdown.png \
	pkg/shell/images/category-storage.png \
	pkg/shell/images/category-system.png \
	pkg/shell/images/category-users.png \
	pkg/shell/images/avatar-default-48.png \
	pkg/shell/images/avatar-default-128.png \
	pkg/shell/images/play.png \
	pkg/shell/images/eject.png \
	pkg/shell/images/server-large.png \
	pkg/shell/images/stop.png \
	pkg/shell/images/dialog-error.png \
	pkg/shell/images/face-smile.png \
	pkg/shell/images/hammer.gif \
	pkg/shell/images/storage-disk.png \
	$(NULL)

# -----------------------------------------------------------------------------

CHECK_HTML = \
	pkg/shell/test-dummy.html \
	pkg/shell/test-util.html \
	pkg/shell/test-chan.html \
	pkg/shell/test-journal-renderer.html \
	pkg/shell/test-rest.html \
	pkg/shell/test-spawn.html \
	pkg/shell/test-dbus.html \
	$(NULL)

TESTS += $(CHECK_HTML)

# ----------------------------------------------------------------------------------------------------

lang/%.json : $(top_srcdir)/po/%.po
	$(AM_V_GEN) mkdir -p lang && $(PO2JSON) -p $(top_srcdir)/po/$*.po > lang/$*.json

CLEANFILES += \
	cockpit.js \
	$(NULL)

EXTRA_DIST += \
	$(cockpit_js_PARTS) \
	$(shell_DATA) \
	$(shellimages_DATA) \
	$(CHECK_HTML) \
	pkg/shell/shell.html \
	$(NULL)