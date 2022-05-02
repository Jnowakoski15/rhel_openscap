# Ansible Collection - rhel_openscap

This content is designed for use with the RHEL workshop found at https://github.com/ansible/workshops

## CLI setup
**Note:** Fork this project into a repository you can write to.  Just change the git URL in this example to match your repository. 


On your VSCode host, which is running on the same endpoint as Controller:

Clone this content to ~/rhel_openscap via:

 `cd && git clone https://github.com/Jnowakoski15/rhel_openscap.git`

Copy the workshop inventory into the project for cli use:

`cd ~/rhel_openscap && cp ~/lab_inventory/hosts .`

Add the following entry to the inventory to ensure hosts apply `group_vars/rhel.yml`:
```
[rhel:children]
web
```

If you are not student1 in your workshop, you will need to change `student_id` in `group_vars/rhel.yml`

An ansible-navigator.yml is provided for use with the command line tool, ansible-navigator. 
  - https://github.com/ansible/ansible-navigator
  - https://ansible-navigator.readthedocs.io/

### CLI Examples
An example invocation targeting `node1`, using the mode `stdout`, which provides output like `ansible-playbook`.

`ansible-navigator run rhel_openscap.yml -i hosts -e "target=node1" -m stdout`

This example will generate `~/rhel_openscap/node1-report.html` 

You can right click the file in VSCode's file explorer, and select download, to open the report in your browser.

Another example, which generates an xml results file and uses it to generate a playbook which remediates those results:

`ansible-navigator run rhel_openscap.yml -i hosts -e "target=node1 generate_remediation=true" -m stdout --skip-tags report`

**Note:** The `ansible-navigator.yml` config defines the runtime container image as `ee-supported-rhel8`.  Apply the same Execution Environment container image to your job template in Controller.

**TODO:**
Controller Setup/Examples

