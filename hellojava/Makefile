PROJECT = hello

SRCDIR = src
BUILDDIR = build
CLASSDIR = $(BUILDDIR)/classes
JARDIR = $(BUILDDIR)/jar

CLASSES = com/michiow/hello/Hello.class \
	  com/michiow/hello/HelloApp.class

CLASSFILES = $(addprefix $(CLASSDIR)/, $(CLASSES))

JARFILE = $(JARDIR)/$(PROJECT).jar

ENTRY = com.michiow.hello.HelloApp

vpath %.java $(SRCDIR)

$(CLASSDIR)/%.class: %.java
	javac -d $(CLASSDIR) -cp $(CLASSDIR) $<

.PHONY: all
all: $(CLASSFILES)

$(CLASSFILES): | $(CLASSDIR)

$(CLASSDIR):
	mkdir -p $@

.PHONY: jar
jar: $(JARFILE)

$(JARFILE): $(CLASSFILES) | $(JARDIR)
	jar cfe $@ $(ENTRY) -C $(CLASSDIR) .

$(JARDIR):
	mkdir -p $@

.PHONY: run
run: $(CLASSFILES)
	java -cp $(CLASSDIR) $(ENTRY)

.PHONY: clean
clean:
	-rm -rf $(CLASSDIR)
	-rm -f $(JARFILE)

