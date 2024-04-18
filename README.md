class agent1 extends uvm_agent;
`uvm_component_utils(agent1)
driver drv;
monitor1 mon;
sequencer sqncr;

function new(string name, uvm_component parent);
super.new(name,parent);
endfunction

function void build_phase(uvm_phase phase);
super.build_phase(phase);
drv=driver::type_id::create("drv",this);
mon=monitor1::type_id::create("mon",this);
sqncr=sequencer::type_id::create("sqncr",this);
`uvm_info(get_name(),"Agent1 build phase with none",0);
`uvm_info(get_name(),"Agent1 build phase with medium",100);
`uvm_info(get_name(),"Agent1 build phase with low",200);
`uvm_info(get_name(),"Agent1 build phase with high",300);
`uvm_info(get_name(),"Agent1 build phase with full",400);
`uvm_info(get_name(),"Agent1 build phase with debug",500);
endfunction

function void connect_phase(uvm_phase phase);
super.connect_phase(phase);
drv.seq_item_port.connect(sqncr.seq_item_export);
endfunction

task run_phase(uvm_phase phase);
super.run_phase(phase);
`uvm_info(get_name(),"Agent1 run phase with none",0);
`uvm_info(get_name(),"Agent1 run phase with none",UVM_LOW);
`uvm_info(get_name(),"Agent1 run phase with none",UVM_MEDIUM);
`uvm_info(get_name(),"Agent1 run phase with none",UVM_HIGH);
`uvm_info(get_name(),"Agent1 run phase with none",UVM_FULL);
`uvm_info(get_name(),"Agent1 run phase with none",UVM_DEBUG);
endtask
endclass
