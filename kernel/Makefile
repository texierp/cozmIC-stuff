GCC?=gcc
DTC?=dtc
DTC_OPTIONS?=-@

OBJECTS:= $(patsubst %.dts,%.dtbo,$(wildcard overlays/*.dts overlays/*/*.dts))

%.pre.dts: %.dts
	$(GCC) -E -nostdinc -I$(CURDIR)/include -I$(CURDIR) -x assembler-with-cpp -undef -o $@ $^

%.dtbo: %.pre.dts
	$(DTC) $(DTC_OPTIONS) -I dts -O dtb -o $@ $^

all: $(OBJECTS)

clean:
	rm -f $(OBJECTS)
