# General guidelines
Details on how to use the below templates to configure a Palo Alto device are displayed in the [README.md](https://github.com/kentik/config-snippets/blob/master/README.md) file at the root of this repository

# Palo Alto configuration guidelines
Flow configuration on PanOS is displayed in greater detail on their online documentation portal [HERE](https://docs.paloaltonetworks.com/pan-os/9-0/pan-os-admin/monitoring/netflow-monitoring/configure-netflow-exports)

## Configuration via the PanOS UI
### If using direct, public ingest
#### Create a new KENTIK profile
Go to *Device* &rarr; *Server Profiles* &rarr; *Netflow* &rarr; *Add Profile*
In this profile use these settings:
* *Name*: <KENTIK_PUBLIC_INGEST>
* *Template Refresh Rate*: 30 minutes, 600 packets 
* *Active Timeout*: 1 Minute
* *PanOS Field Types*:
  * App-ID
  * User-ID
* *Collector Name*: <KENTIK>
* *Collector Netflow Server*: {{kentik_ingest_ip_from_UI}}
* *Port*: {{kentik_ingest_UDP_port_from_UI}}

#### Enable Flow Collection on interfaces
Got to *Network* &rarr; *Interfaces* &rarr; *Ethernet*: <KENTIK_FLOW>

### If using the Kentik Flow Proxy
Go to *Device* &rarr; *Server Profiles* &rarr; *Netflow* &rarr; *Add Profile*
In this profile use these settings:
* *Name*: <KENTIK_FLOW_PROXY_INGEST>
* *Template Refresh Rate*: 30 minutes, 600 packets 
* *Active Timeout*: 1 Minute
* *PanOS Field Types*:
  * App-ID
  * User-ID
* *Collector Name*: <KENTIK>
* *Collector Netflow Server*: <kentik_flow_proxy_agent_IP>
* *Port*: 9995 (update with your own if your KProxy setup uses a non-default, custom-set port to ingest flow records)

#### Enable Flow Collection on interfaces
Got to *Network* &rarr; *Interfaces* &rarr; *Ethernet*: <KENTIK_FLOW>
