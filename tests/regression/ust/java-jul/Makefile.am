if BUILD_JAVA_AGENT

noinst_SCRIPTS = test_java_jul JTestLTTng.java
EXTRA_DIST = test_java_jul JTestLTTng.java

if HAVE_JAVA_JDK
JCC=$(JAVA_JDK)/bin/javac
else
JCC=javac
endif

AGENT_JAR_FILE=$(java_agent_jar_path)

all-local: JTestLTTng.class

%.class: %.java
	$(JCC) -d "$(builddir)" -cp "$(AGENT_JAR_FILE):." $<

JTestLTTng.class: JTestLTTng.java

all-local:
	@if [ x"$(srcdir)" != x"$(builddir)" ]; then \
		for script in $(EXTRA_DIST); do \
			cp -f $(srcdir)/$$script $(builddir); \
		done; \
	fi

clean-local:
	rm -f *.class
	@if [ x"$(srcdir)" != x"$(builddir)" ]; then \
		for script in $(EXTRA_DIST); do \
			rm -f $(builddir)/$$script; \
		done; \
	fi

endif # BUILD_JAVA_AGENT
