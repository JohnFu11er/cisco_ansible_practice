<h1> cisco_ansible_practice </h1>
This is a project that demonstrates the interconnected nature of Jinja2 templates being dynamically populated by an Ansible playbook that parses the variable data from an imported .yml file.<br>
<br>
<b>PROCESS (main_build.yml)</b><br>
<br>
1. (TASK 1) The main_build.yml file imports the device_vars.yml.<br>
2. (TASK 2) The main_build.yml file creates the ./finished_router_configs directoty that will be used to store the generated router config files from "TASK 3".<br>
3. (TASK 3) The main_build.yml file uses the variables imported from the device_vars.yml file to populate the jinja2 template named router_config.j2<br>
4. (TASK 3) The router_config.j2 file processes child jinja templates such as interfaces.j2 or eigrp.j2.  After these child templates are processed, their contents are written to the parent jinja2 template router_config.j2.<br>
5. (TASK 3) Once the router_config.j2 template has processed all it's child templates, and populated any variable assignements, its contents is written to the ./finished_router_config/ into a file that correlates to the router's hostname stored in the device_vars.yml file.
