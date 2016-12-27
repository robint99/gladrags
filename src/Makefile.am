
SUBDIRS =

applet_SCRIPTS = gladrags.py log_it.py prefs_dlg.py about.py

appletdir = $(libdir)/mate-applets/gladrags/

APPLET_LOCATION = $(appletdir)gladrags.py

appletsdir       = $(datadir)/mate-panel/applets
applets_in_files = org.mate.panel.gladrags.mate-panel-applet
applets_DATA     = $(applets_in_files:.mate-panel-applet.in=.mate-panel-applet)

if WITH_GTK3_SET
do_substitution = $(AM_V_GEN)sed \
		-e 's,[@]pythondir[@],$(pythondir),g' \
		-e 's,[@]PACKAGE[@],$(PACKAGE),g' \
	  	-e 's,[@]VERSION[@],$(VERSION),g' \
	    -e 's,[@]LOCATION[@],$(appletdir),g' \
	    -e 's,[@]localedir[@],$(datadir)/locale,g'
else
do_substitution = $(AM_V_GEN)sed \
		-e 's,[@]pythondir[@],$(pythondir),g' \
		-e 's,[@]PACKAGE[@],$(PACKAGE),g' \
	  	-e 's,[@]VERSION[@],$(VERSION),g' \
	    -e 's,[@]LOCATION[@],$(appletdir),g' \
	    -e 's,[@]localedir[@],$(datadir)/locale,g' \
	    -e 's,build_gtk2 = False,build_gtk2 = True,g'
endif

#$(applets_in_files): $(applets_in_files).in Makefile
#	$(AM_V_GEN)sed \
#		-e "s|\@LOCATION\@|$(appletdir)|" \
#		-e "s|\@pythondir\@|$(pythondir)|" \
#	  	-e "s|\@PACKAGE\@|$(PACKAGE)|" \
#	  	-e "s|\@VERSION\@|$(VERSION)|" \
#		$< > $@

#%.mate-panel-applet.in: %.mate-panel-applet.in.in Makefile
#	$(AM_V_GEN)sed \
#		-e "s|\@LOCATION\@|$(appletdir)|" \
#		-e "s|\@pythondir\@|$(pythondir)|" \
#	  	-e "s|\@PACKAGE\@|$(PACKAGE)|" \
#	  	-e "s|\@VERSION\@|$(VERSION)|" \
#		-e "s|\@localdir\@|$(datadir)//locale|" \
#		$< > $@

#@PANEL_INTLTOOL_MATE_PANEL_APPLET_RULE@

servicedir       = $(datadir)/dbus-1/services
service_in_files = org.mate.panel.applet.gladragsAppletFactory.service.in
service_DATA     = $(service_in_files:.service.in=.service)

imagedir	 = $(appletdir)
image_DATA	 = tuxedo_light.png \
                   tuxedo_dark.png \
                   tux1_light.png \
                   tux1_dark.png
#		   sahsd.png \
#		   boinc.png

#%.gschema.xml.in: %.gschema.xml.in.in Makefile
#	$(AM_V_GEN)sed -e 's^\@GETTEXT_PACKAGE\@^$(GETTEXT_PACKAGE)^g' < $< > $@
#

gsettings_SCHEMAS = org.mate.panel.applet.gladrags.gschema.xml

#
#@INTLTOOL_XML_NOMERGE_RULE@
#@GSETTINGS_RULES@

#$(gsettings_SCHEMAS).in: $(gsettings_SCHEMAS).in.in Makefile
#	$(AM_V_GEN)sed -e 's^\@GETTEXT_PACKAGE\@^$(GETTEXT_PACKAGE)^g' \
# 		       -e "s|\@LOCATION\@|$(libexecdir)|" \
#		       < $< > $@

org.mate.panel.applet.gladragsAppletFactory.service: $(service_in_files)
	$(AM_V_GEN)sed \
		-e "s|\@LOCATION\@|$(APPLET_LOCATION)|" \
		$< > $@

org.mate.panel.gladrags.mate-panel-applet: $(applet_in_files)
	$(do_substitution) < $(srcdir)/org.mate.panel.gladrags.mate-panel-applet.in > org.mate.panel.gladrags.mate-panel-applet

#dock_about.py: dock_about.in Makefile
#	$(do_substitution) < $(srcdir)/dock_about.in > dock_about.py
#	chmod +x dock_about.py
#
#dock_prefs.py: dock_prefs.in Makefile
#	$(do_substitution) < $(srcdir)/dock_prefs.in > dock_prefs.py
#	chmod +x dock_prefs.py

log_it.py: log_it.in Makefile
	$(do_substitution) < $(srcdir)/log_it.in > log_it.py
	chmod +x log_it.py

gladrags.py: gladrags.in Makefile
	$(do_substitution) < $(srcdir)/gladrags.in > gladrags.py
	chmod +x gladrags.py

prefs_dlg.py: prefs_dlg.in Makefile
	$(do_substitution) < $(srcdir)/prefs_dlg.in > prefs_dlg.py
	chmod +x prefs_dlg.py

about.py: about.in Makefile
	$(do_substitution) < $(srcdir)/about.in > about.py
	chmod +x about.py

applet_PYTHON = \
		     gladrags.py 

CLEANFILES = $(applet_SCRIPTS) \
	     org.mate.panel.applet.gladragsFactory.service \
	     org.mate.panel.gladrags.mate-panel-applet

#	     dock_about.in \ add this to extra dist
#	     $(gsettings_SCHEMAS) \ add this to extra dist

EXTRA_DIST = gladrags.in \
             prefs_dlg.in \
             log_it.in \
             about.in \
	     $(applets_in_files) \
	     $(gsettings_SCHEMAS) \
	     $(service_in_files) \
             $(image_DATA) 

