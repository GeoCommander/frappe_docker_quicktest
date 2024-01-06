## Main tips

**docker build**
if issues with building docker image begins, use: docker build --no-cache \
NO WINOWS WSL during docker build command execution
--tag=custom/hrms:latest does not work use: --tag=custom/hrms:1.0.0 \
if confused with app.json file setup then take a look an simple example file on rako-erpnext

**compose file:**
use: .yaml file for whatever reason .yml did not work
use: mariadb 11.2 although it will make database health look yellow
include: depends_on: ["backend"] for queue-short and scheduler
use: bench --site frontend install-app hrms; replace hrms with appropriate INSTALLED ON IMAGE APP (need to build the image)

**portainer**
delete old volumes before initial deployment
wait for 3 minutes after first deploymenet for data to inialize. if stopped early it wont initialize properly
stop container after 3 minutes and redeploy (stop and start the stack)
