
DIR := ../src

controller.vvp: ddr3.v $(DIR)/ddr3_controller.v tb_controller.v prim_sim.v
	iverilog -o controller.vvp -D SIM -D den1024Mb -D sg25 -D x16 -g 2012 tb_controller.v ddr3.v $(DIR)/ddr3_controller.v prim_sim.v

controller: controller.vvp

run.controller: controller.vvp
	if not exist tmp mkdir tmp
	vvp controller.vvp

# Vanilla Micron DDR3 simulation
ddr3.vvp: ddr3.v 1024*.vh tb.v subtest.vh
	iverilog -o ddr3.vvp -D den1024Mb -D sg25 -D x16 -g 2012 tb.v ddr3.v

ddr3: ddr3.vvp

run.ddr3: ddr3.vvp
	if not exist tmp mkdir tmp
	vvp ddr3.vvp

# Misc
tag: *.v *.vh
	ctags -R *.v 1024*

clean:
	del *.vvp

