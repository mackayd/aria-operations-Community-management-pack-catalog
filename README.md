# Aria Operations Community Management Pack Catalog

A central catalog for community VMware Aria Operations management packs published by [Drew Mackay](https://github.com/mackayd).

This repository does **not** contain the management pack source files or PAK installers directly. It is intended to act as a clean landing page that links to the individual management pack repositories, where the installable PAK files, Management Pack Builder JSON exports, icon tooling, release notes, and detailed usage guidance are maintained.

> These are community management packs and supporting tools. They are not official Broadcom, VMware, Dell, HPE, or Oracle supported products. Validate each pack in a lab before using it in production.

---

## Management Pack Catalog

| Management Pack | Vendor / Technology | Primary API | Main Purpose | Repository |
|---|---|---|---|---|
| Dell DataDomain / PowerProtect DD Management Pack | Dell DataDomain, PowerProtect DD, DDVE | Dell DD REST API | Monitor DD system health, capacity, compression, file systems, MTrees, DDBoost, networking, services, licensing, disk inventory, replication, and active alerts. | [aria-operations-dell-datadomain-management-pack](https://github.com/mackayd/aria-operations-dell-datadomain-management-pack) |
| HPE iLO Management Pack | HPE iLO / ProLiant server hardware | Redfish API | Monitor iLO and server hardware inventory, health, firmware, power, thermal, chassis, processor, memory, storage, fan, PSU, and temperature data where exposed by the endpoint. | [aria-operations-HPE-ILO-management-pack](https://github.com/mackayd/aria-operations-HPE-ILO-management-pack) |
| Dell Unity Community Management Pack | Dell EMC Unity, Unity XT, UnityVSA | Dell Unity REST API | Monitor Unity storage system health, pools, storage resources, file systems, NAS servers, host mappings, physical hardware, ports, replication sessions, and alerts. | [aria-operations-dell-unity-community-management-pack](https://github.com/mackayd/aria-operations-dell-unity-community-management-pack) |
| Dell OpenManage Enterprise Community Management Pack | Dell OpenManage Enterprise 4.x | Dell OME REST API | Monitor Dell OME-managed server inventory, health, power, temperature, operating system information, location information, and hardware component state. | [aria-operations-dell-OpenManage-Community-management-pack](https://github.com/mackayd/aria-operations-dell-OpenManage-Community-management-pack) |
| Brocade Fabric OS Community Management Pack | Dell Connectrix B-Series / Brocade Fabric OS | Fabric OS REST API | Monitor Fibre Channel fabrics, switches, ports, connected endpoints, transceivers, sensors, fans, power supplies, performance, congestion, health, and alerts. | [aria-operations-Brocade-Fabric-OS-Community-management-pack](https://github.com/mackayd/aria-operations-Brocade-Fabric-OS-Community-management-pack) |
| HPE OneView Community Management Pack | HPE OneView 10.2+ managed infrastructure | HPE OneView REST API | Monitor OneView inventory, health, capacity, configuration, relationships, server hardware, enclosures, networks, storage resources, firmware baselines, and alerts. | [aria-operations-HPE-OneView-Community-management-pack](https://github.com/mackayd/aria-operations-HPE-OneView-Community-management-pack) |
| Oracle Linux Virtualization Manager Community Management Pack | Oracle Linux Virtualization Manager 4.5 | OLVM Engine REST API | Monitor OLVM inventory, host and virtual-machine performance, storage capacity, resource relationships, and platform events. | [aria-operations-Oracle-Linux-Virtualization-Community-management-pack](https://github.com/mackayd/aria-operations-Oracle-Linux-Virtualization-Community-management-pack) |

---

## Additional Resources

### Unity API Emulator

If the Dell UnityVSA Community Edition storage appliance or licence activation process is unavailable, the Unity API Emulator can be used as a local Unity-style REST endpoint for lab and development workflows.

| Resource | Purpose | Repository |
|---|---|---|
| Unity API Emulator | Python-based Dell Unity / Unisphere REST API emulator for testing scripts, integrations, and VMware Aria Operations Management Pack Builder collection logic when a licensed UnityVSA appliance is unavailable. | [Unity-API-Emulator](https://github.com/mackayd/Unity-API-Emulator) |

> The Unity API Emulator is a mock API server. It is useful for testing request construction, authentication flow, response parsing, and collection logic. It must not be treated as a replacement for validation against a real Dell Unity array.

---

## How to Use This Catalog

1. Choose the management pack that matches the platform you want to monitor.
2. Open the linked repository.
3. Review the repository README for prerequisites, supported API coverage, installation notes, known limitations, and validation status.
4. Download the recommended `.pak` file from the repository.
5. Install the `.pak` into VMware Aria Operations.
6. Add an adapter / integration account in Aria Operations using the target platform hostname, port, credentials, and SSL settings.
7. Run **Test Connection** and allow one or more collection cycles to complete.

---

## Typical Aria Operations PAK Installation Flow

The exact menu names vary slightly between Aria Operations versions, but the normal process is:

1. Log in to VMware Aria Operations with an account that can install management packs.
2. Browse to one of the following areas, depending on version:
   - `Administration > Integrations > Repository`
   - `Administration > Control Panel > Management Packs`
   - `Data Sources > Integrations > Repository`
3. Upload the `.pak` file from the selected repository.
4. Accept the installation prompts.
5. Wait for the management pack installation to complete across the Aria Operations cluster.
6. Go to the integrations / accounts area.
7. Add a new account for the installed adapter.
8. Enter the target endpoint details and credentials.
9. Run **Test Connection**.
10. Save the adapter instance and validate discovered objects, metrics, relationships, dashboards, and alerts.

---

## Editing or Rebuilding a Pack

Most of the linked repositories include a Management Pack Builder JSON export. This allows the pack to be reviewed, modified, or rebuilt using VMware Aria Operations Management Pack Builder.

General workflow:

1. Clone or download the relevant management pack repository.
2. Locate the Management Pack Builder JSON file, usually under a folder such as `mp-builder`, `ImportJSON-AriaMP-builder`, or similar.
3. Open Management Pack Builder.
4. Import the JSON export.
5. Review adapter definitions, object types, relationships, metrics, properties, alerts, dashboards, and collection logic.
6. Make the required changes.
7. Build a new `.pak` file.
8. Test in a lab Aria Operations environment before publishing or deploying into production.

---

## Standard Repository Contents

The individual management pack repositories commonly include some or all of the following:

| Item | Purpose |
|---|---|
| `README.md` | Detailed documentation for that specific pack. |
| `LICENSE` | Licence information for the repository. |
| `PAK-Release` | Ready-to-install Aria Operations `.pak` files. |
| `mp-builder`, `ImportJSON-AriaMP-builder`, or similar | Importable Management Pack Builder JSON source. |
| `icons`, `Images`, or custom icon folders | Resource icons, adapter icons, topology images, and contact sheets. |
| `tools` or custom icon tooling | Scripts used to post-process PAK files, inject custom icons, or preserve naming/layout behaviour. |

Some repositories include both a standard Management Pack Builder-generated PAK and an additional icon-injected PAK. Where an icon-injected PAK is provided, the individual repository README explains which PAK is recommended.

---


## Support and Contribution Model

These repositories are community resources. They are intended to help infrastructure engineers, consultants, and lab users extend VMware Aria Operations visibility into platforms that may not have a suitable native or vendor-supplied management pack.

For issues or improvements:

1. Open an issue in the specific management pack repository rather than this catalog repository.
2. Include the Aria Operations version, target platform version, API endpoint details, error message, and any relevant logs.
3. Avoid posting credentials, tokens, session IDs, customer names, internal FQDNs, or public IP addresses in issues.
4. For feature requests, describe the target API endpoint, expected object model, metrics/properties required, and intended dashboard or alert use case.

---

## Repository Scope

This catalog currently links only to the following Aria Operations community management pack repositories:

- [aria-operations-dell-datadomain-management-pack](https://github.com/mackayd/aria-operations-dell-datadomain-management-pack)
- [aria-operations-HPE-ILO-management-pack](https://github.com/mackayd/aria-operations-HPE-ILO-management-pack)
- [aria-operations-dell-unity-community-management-pack](https://github.com/mackayd/aria-operations-dell-unity-community-management-pack)
- [aria-operations-dell-OpenManage-Community-management-pack](https://github.com/mackayd/aria-operations-dell-OpenManage-Community-management-pack)
- [aria-operations-Brocade-Fabric-OS-Community-management-pack](https://github.com/mackayd/aria-operations-Brocade-Fabric-OS-Community-management-pack)
- [aria-operations-HPE-OneView-Community-management-pack](https://github.com/mackayd/aria-operations-HPE-OneView-Community-management-pack)
- [aria-operations-Oracle-Linux-Virtualization-Community-management-pack](https://github.com/mackayd/aria-operations-Oracle-Linux-Virtualization-Community-management-pack)

Additional supporting resources:

- [Unity-API-Emulator](https://github.com/mackayd/Unity-API-Emulator)

