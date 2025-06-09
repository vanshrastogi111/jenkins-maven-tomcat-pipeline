# 📦 Apache Tomcat Hands-On

**Apache Tomcat** is an open-source Java Servlet and JSP container developed by the Apache Software Foundation. It's widely used for deploying Java-based web applications due to its simplicity, cross-platform compatibility, and robust performance.



## 🛠 Real-World Scenario: E-Commerce Web Application

A company is building a Java-based e-commerce site using **Servlets** and **JSP**. Tomcat is used at each stage of the application lifecycle:

- **Development**: Developers use a local Tomcat server to deploy and test their Java web app.
- **Testing**: QA teams deploy the `.war` file on a shared Tomcat instance to validate features.
- **Staging**: The app is moved to a staging server configured similarly to production.
- **Production**: The `.war` is deployed to a production-grade Tomcat server.
- **Scaling**: Load balancers and clustered Tomcat nodes handle increasing traffic.
- **Monitoring**: Tomcat's GUI tools help monitor server health and application status.
- **Security**: SSL/TLS and role-based access protect the application.

---

## ⚙️ Commands to Set Up Tomcat

```bash
# Step 1: Download and extract Tomcat
cd /opt
sudo wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.65/bin/apache-tomcat-9.0.65.tar.gz
sudo tar -xvf apache-tomcat-9.0.65.tar.gz

# Step 2: Add admin user
cd /opt/apache-tomcat-9.0.65/conf
sudo vi tomcat-users.xml

# Add inside <tomcat-users> block:
<user username="admin" password="admin1234" roles="admin-gui,manager-gui"/>

# Step 3: Enable access to manager/host-manager from any IP
sudo vi /opt/apache-tomcat-9.0.65/webapps/manager/META-INF/context.xml
# Comment out the Valve restricting remote access:
<!--
<Valve className="org.apache.catalina.valves.RemoteAddrValve"
       allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
-->

sudo vi /opt/apache-tomcat-9.0.65/webapps/host-manager/META-INF/context.xml
# Comment similarly:
<!--
<Valve className="org.apache.catalina.valves.RemoteAddrValve"
       allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
-->

# Step 4: Create shortcuts to manage Tomcat
sudo ln -s /opt/apache-tomcat-9.0.65/bin/startup.sh /usr/bin/startTomcat
sudo ln -s /opt/apache-tomcat-9.0.65/bin/shutdown.sh /usr/bin/stopTomcat

# Step 5: Restart Tomcat
sudo stopTomcat
sudo startTomcat
