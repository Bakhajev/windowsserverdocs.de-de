# [Remotedesktopdienste](welcome-to-rds.md)
## [Erste Schritte](rds-get-started.md)
### [Neues in RDS](rds-whats-new.md)
### [Unterstützte Konfigurationen für RDS](rds-supported-config.md)
### [Unterstützte Sicherheitskonfigurationen für Windows10 VDI](rds-vdi-supported-config.md)
### [Planungsposter für Remotedesktopdienste](rds-poster.md)
### [Remote Desktop Services – Hosting-Partner](rds-hosting-partners.md)
## [Planen und Entwerfen](rds-plan-and-design.md)
### [Erstellen überall](rds-plan-build-anywhere.md)
### [Zusatzaufwand für andere Arten von Benutzern](rds-plan-cater-to-users.md)
### [Zugriff von jedem beliebigen Standort](rds-plan-access-from-anywhere.md)
### [Hohe Verfügbarkeit](rds-plan-high-availability.md)
### [Multi-Factor Authentication](rds-plan-mfa.md)
### [Sichern des Datenspeichers](rds-plan-secure-data-storage.md)
### [Auswählen der Grafikrenderingtechnologie](rds-graphics-virtualization.md)
### [Verbinden von einem beliebigen Gerät aus](rds-plan-connect-from-any-device.md)
### [Wählen der Bezahlungsart](rds-plan-choose-how-you-pay.md)
### [Office 2016 in RDS- und VDI-Bereitstellungen](https://docs.microsoft.com/deployoffice/rds-office-vdi-rdsh)
#### [Verwenden von Outlook-Suche in nicht persistenten Umgebungen](https://docs.microsoft.com/deployoffice/rds-outlook-search)
#### [OneDrive for Business und VDI-Umgebungen](https://docs.microsoft.com/deployoffice/rds-onedrive-business-vdi)
### [Referenzarchitektur für das Desktophosting](Desktop-Hosting-Reference-Architecture.md)
#### [Architektur der Remotedesktopdienste](Desktop-hosting-logical-architecture.md)
#### [Desktophosting-Dienst](Desktop-hosting-service.md)
#### [Remotedesktopdienste – Rollen](rds-roles.md)
#### [Azure-Dienste und Überlegungen zum Desktophosting](Azure-services-and-considerations-for-desktop-hosting.md)
## [Erstellen und Bereitstellen](rds-build-and-deploy.md)
### [Bereitstellen einer Prüfung des Konzepts RDS-Umgebung mit ARM und Azure Marketplace](rds-in-azure.md)
### [Migrieren von Remotedesktopdienste-Bereitstellungen zu Windows Server 2016](migrate-rds-role-services.md)
### [Migrieren von Remotedesktopdienste-Clientzugriffslizenzen (RDS-CALs)](migrate-rds-cals.md)
### [Upgrade von Remotedesktopdienste-Bereitstellungen auf Windows Server 2016](upgrade-to-rds.md)
#### [Upgrade von Remotedesktop-Sitzungshostservern](upgrade-to-rdsh.md)
#### [Upgrade von Remotedesktop-Virtualisierungs-Hostservern](upgrade-to-rdvh.md)
### [Bereitstellen einer Remotedesktopdienste-Infrastruktur](rds-deploy-infrastructure.md)
### [Erstellen und Bereitstellen einer Remotedesktopdienste-Sammlung](rds-create-collection.md)
### [Einrichten des Remotedesktop-Webclients für Ihre Benutzer](clients/remote-desktop-web-client-admin.md)
### [Einrichten der E-Mail-Erkennung für Ihre Benutzer](rds-email-discovery.md)
### [Lizenzieren Ihrer Remotedesktopbereitstellung](rds-client-access-license.md)
#### [Aktivieren des Lizenzservers](rds-activate-license-server.md)
#### [Installieren der RDS-CALs auf dem Lizenzserver](rds-install-cals.md)
#### [Nachverfolgen der in Ihrer Bereitstellung verwendeten CALs](rds-track-cals.md)
### [Integrieren von Azure-Dienste](rds-integrate-with-azure.md)
#### [Hier erfahren Sie, wie mit Multi-Factor Authentication mit RDS](/azure/multi-factor-authentication/nps-extension-remote-desktop-gateway)
#### [Integration von Azure Active Directory Domain Services mit der RDS-Bereitstellung](rds-azure-adds.md)
#### [Veröffentlichen von Remotedesktop mit Azure AD-Anwendungsproxy](/azure/active-directory/application-proxy-publish-remote-desktop)
### Erweitern der RDS-Umgebung für hohe Verfügbarkeit
#### [Skalieren einer vorhandenen RDS-Sammlung mit einer Farm RD-Sitzungshostserver](rds-scale-rdsh-farm.md)
#### [Hinzufügen von hoher Verfügbarkeit der RD Connection Broker-Infrastruktur](rds-connection-broker-cluster.md)
#### [Hinzufügen von hoher Verfügbarkeit der RD Web- und RD-Gateway Webfront](rds-rdweb-gateway-ha.md)
#### [Bereitstellen eines auf zwei Knoten und „Storage Spaces Direct“ basierenden Dateisystems für die UPD-Speicherung](rds-storage-spaces-direct-deployment.md)
#### [Bereitstellen und Verwalten einer persönlichen Sitzungsdesktopumgebung](rds-personal-session-desktops.md)
#### [Erstellen von VMs für RDS](rds-prepare-vms.md)
### [Einrichten der Wiederherstellung für der RDS-Umgebung](rds-disaster-recovery.md)
#### [Erstellen einer Geo redundant RDS-Bereitstellung](rds-multi-datacenter-deployment.md)
#### [Einrichten von Azure Site Recovery für RDS](rds-disaster-recovery-with-azure.md)
##### [Aktivieren der Wiederherstellung für RDS-Komponenten](rds-enable-dr-with-asr.md)
##### [Erstellen des Wiederherstellungsplans](rds-disaster-recovery-plan.md)

## [Ausführen und Abstimmen](rds-run-and-tune.md)
### [Einrichten und Konfigurieren von RemoteFX vGPU für Remotedesktopdienste](rds-remotefx-vgpu.md)
### [Verwalten von persönlichen desktop-Sitzung Sammlungen](rds-manage-personal-collection.md)
### [Empfohlene Konfiguration für VDI-Desktops](rds-vdi-recommendations.md)
### [Optimieren von Windows 10, Version 1803, für die Rolle für die virtuelle Desktopinfrastruktur (Virtual Desktop Infrastructure, VDI)](rds-vdi-recommendations-1803.md)
### [Verwalten von Benutzern in Ihrer RDS-Sammlung](rds-user-management.md)
### [Anpassen der RDS Titel "Arbeitsressourcen" mithilfe von PowerShell unter Windows Server](rds-work-resources.md)
### [Diagnostizieren von app-Leistungsprobleme mit Leistungsindikatoren](rds-rdsh-performance-counters.md)

## [Zusätzliche Unterstützung zum Thema Remotedesktop](rds-get-support.md)
## [Remotedesktopclients](clients/remote-desktop-clients.md)
### Allgemeine Informationen
#### [Welcher Client eignet sich am besten für Sie?](clients/remote-desktop-app-compare.md)
#### [Remotedesktop-URI-Schema](clients/remote-desktop-uri.md)
#### [Remotedesktopclient – Häufig gestellte Fragen](clients/remote-desktop-client-faq.md)
#### [Datenschutzeinstellungen für verwaltete Apps und Desktops](clients/remote-privacy-settings.md)
#### [Problembehandlung für Remotedesktopverbindungen](clients/troubleshoot-remote-desktop-connections.md)
### Remotedesktopclient für Windows
#### [Erste Schritte](clients/windows.md)
#### [Neuigkeiten im Windows-Client](clients/windows-whatsnew.md)
### Remotedesktopclient für Android
#### [Erste Schritte](clients/remote-desktop-android.md)
#### [Neuigkeiten im Android-Client?](clients/android-whatsnew.md)
### Remotedesktopclient für iOS
#### [Erste Schritte](clients/remote-desktop-ios.md)
#### [Neuigkeiten im iOS-Client](clients/ios-whatsnew.md)
### Remotedesktopclient für Mac
#### [Erste Schritte](clients/remote-desktop-mac.md)
#### [Neuigkeiten im MacOS-Client](clients/mac-whatsnew.md)
### Remote Desktop-Webclient
#### [Zugriff auf den Remotedesktop-Webclient](clients/remote-desktop-web-client.md)
#### [Neuigkeiten im Webclient?](clients/web-client-whatsnew.md)
### Einrichten Ihres PCs für Remotedesktop
#### [Unterstützte PCs](clients/remote-desktop-supported-config.md)
#### [Gewähren des Zugriffs auf Ihren PC für Remotedesktop](clients/remote-desktop-allow-access.md)
#### [Gewähren des Zugriffs auf Ihren PC vor außerhalb Ihres Netzwerks](clients/remote-desktop-allow-outside-access.md)
#### [Ändern des RD-Abhörports auf Ihrem PC](clients/change-listening-port.md)