ADDIN_BUILD = $(top_builddir)/build/AddIns/MonoDevelop.Debugger.Soft
ASSEMBLY = $(ADDIN_BUILD)/MonoDevelop.Debugger.Soft.AspNet.dll

DEPS =  \
	$(top_builddir)/build/AddIns/MonoDevelop.AspNet/MonoDevelop.AspNet.dll \
	$(top_builddir)/build/AddIns/MonoDevelop.Debugger.Soft/Mono.Debugger.Soft.dll \
	$(top_builddir)/build/AddIns/MonoDevelop.Debugger.Soft/Mono.Debugging.Soft.dll \
	$(top_builddir)/build/AddIns/MonoDevelop.Debugger.Soft/MonoDevelop.Debugger.Soft.dll \
	$(top_builddir)/build/AddIns/MonoDevelop.Debugger/MonoDevelop.Debugger.dll \
	$(top_builddir)/build/bin/Mono.Debugging.dll \
	$(top_builddir)/build/bin/Mono.TextEditor.dll \
	$(top_builddir)/build/bin/MonoDevelop.Core.dll \
	$(top_builddir)/build/bin/MonoDevelop.Ide.dll

REFS =  \
	$(GLIB_SHARP_LIBS) \
	$(GTK_SHARP_LIBS) \
	-r:System \
	-r:System.Core

FILES = AspNetSoftDebuggerEngine.cs

RES = Manifest.addin.xml

all: $(ASSEMBLY) $(ASSEMBLY).mdb $(DATA_FILE_BUILD)

$(ASSEMBLY): $(build_sources) $(build_resources) $(DEPS)
	mkdir -p $(ADDIN_BUILD)
	$(CSC) $(CSC_FLAGS) -debug -out:$@ -target:library $(REFS) $(build_deps) \
		$(build_resources:%=/resource:%) $(build_sources)

$(ASSEMBLY).mdb: $(ASSEMBLY)

check: all

assemblydir = $(MD_ADDIN_DIR)/MonoDevelop.Debugger.Soft
assembly_DATA = $(ASSEMBLY) $(ASSEMBLY).mdb

CLEANFILES = $(ASSEMBLY) $(ASSEMBLY).mdb
EXTRA_DIST = $(FILES) $(RES)

include $(top_srcdir)/Makefile.include

