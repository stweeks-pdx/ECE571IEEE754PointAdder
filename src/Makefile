DEBUG?=false
ifeq ($(DEBUG), true)
	EXTRAFLAGS="+define+DEBUG"
else
	EXTRAFLAGS=
endif

.PHONY: build clean floatpkg barrelshifter expalu bigalu findfirstone normalizer round

build:
	vlib work

clean:
	rm -rf work

floatingpointadder:
	vlog -source -lint $(EXTRAFLAGS) floatingpointpkg.sv fpclass.sv testbench.sv floatingpointadder.sv barrelshifter.sv expalu.sv findfirstone.sv round.sv normalizer.sv bigalu.sv rightshift.sv control.sv
	vsim -c top

floatpkg:
	vlog -source -lint $(EXTRAFLAGS) floatingpointpkg.sv floatingpointpkgtest.sv
	vsim -c top

barrelshifter:
	vlog -source -lint $(EXTRAFLAGS) barrelshifter.sv barrelshiftertest.sv
	vsim -c top

expalu:
	vlog -source -lint $(EXTRAFLAGS) expalu.sv expalutb.sv
	vsim -c top

findfirstone:
	vlog -source -lint $(EXTRAFLAGS) findfirstone.sv ffotb.sv
	vsim -c top

round:
	vlog -source -lint $(EXTRAFLAGS) round.sv roundtb.sv
	vsim -c top

normalizer:
	vlog -source -lint $(EXTRAFLAGS) normalizer.sv barrelshifter.sv findfirstone.sv normalizertb.sv
	vsim -c top

bigalu:
	vlog -source -lint $(EXTRAFLAGS) bigalu.sv bigalutb.sv bigalu-kgm.sv fulladder.sv
	vsim -c top
