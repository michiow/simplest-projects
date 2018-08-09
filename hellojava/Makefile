SRCDIR = src
CLASSDIR = classes

CLASSES = com/michiow/hello/Hello.class \
	  com/michiow/hello/HelloApp.class

CLASSFILES = $(addprefix $(CLASSDIR)/, $(CLASSES))

JAR = hello.jar

ENTRY = com.michiow.hello.HelloApp

vpath %.java $(SRCDIR)

$(CLASSDIR)/%.class: %.java
	javac -d $(CLASSDIR) -cp $(CLASSDIR) $<

.PHONY: all
all: $(CLASSFILES)

$(CLASSFILES): | $(CLASSDIR)

$(CLASSDIR):
	mkdir $@

.PHONY: jar
jar: $(JAR)

$(JAR): $(CLASSFILES)
	jar cfe $@ $(ENTRY) -C $(CLASSDIR) .

.PHONY: run
run: $(CLASSFILES)
	java -cp $(CLASSDIR) $(ENTRY)

.PHONY: clean
clean:
	-rm -rf $(CLASSDIR)
	-rm -f $(JAR)

