### Create Network Application

The main of this project is to develop a project that uses two southbounf plugins (e.g OpenFlow, OVSDB)

         mvn archetype:generate -DarchetypeGroupId=org.opendaylight.controller \
         -DarchetypeArtifactId=opendaylight-startup-archetype \
         -DarchetypeVersion=1.1.2-Beryllium-SR2 \
         -DarchetypeRepository=http://nexus.opendaylight.org/content/repositories/opendaylight.release/ \
         -DarchetypeCatalog=https://nexus.opendaylight.org/content/repositories/opendaylight.release/archetype-catalog.xml

- complete these information 

          Define value for property 'groupId': : org.opendaylight.netapp
          Define value for property 'artifactId': : netapp
          [INFO] Using property: version = 0.1.0-SNAPSHOT
          Define value for property 'package':  org.opendaylight.netapp: : 
          Jan 20, 2017 11:42:51 AM org.apache.velocity.runtime.log.JdkLogChute log
          INFO: FileResourceLoader : adding path '.'
          Define value for property 'classPrefix':  Netapp: : 
          Define value for property 'copyright': : Alioune, BA.
          [INFO] Using property: copyrightYear = 2016
          Confirm properties configuration:
          groupId: org.opendaylight.netapp
          artifactId: netapp
          version: 0.1.0-SNAPSHOT
          package: org.opendaylight.netapp
          classPrefix: Netapp
          copyright: Alioune, BA.
          copyrightYear: 2016

## Config dependencies

- Add properties tags in netapp/impl/pom.xml for setting required version of the used plugins

        <properties>
            <openflowplugin.version>0.2.2-Beryllium-SR2</openflowplugin.version>
            <ovsdb.version>1.2.2-Beryllium-SR1</ovsdb.version>
            <salbindingapi.version>1.3.2-Beryllium-SR2</salbindingapi.version>
        </properties>


- set dependencies netapp/impl/pom.xml

        <!-- begin adding -->
          <dependency>
              <groupId>org.opendaylight.openflowplugin.model</groupId>
              <artifactId>model-flow-base</artifactId>
              <version>${openflowplugin.version}</version>
          </dependency>
          <dependency>
              <groupId>org.opendaylight.openflowplugin.model</groupId>
              <artifactId>model-flow-service</artifactId>
               <version>${openflowplugin.version}</version>
          </dependency>
          <dependency>
              <groupId>org.opendaylight.controller.model</groupId>
              <artifactId>model-inventory</artifactId>
              <version>${salbindingapi.version}</version>
          </dependency>
          <dependency>
              <groupId>org.opendaylight.controller</groupId>
              <artifactId>sal-binding-api</artifactId>
              <version>${salbindingapi.version}</version>
           </dependency>
           <dependency>
              <groupId>org.opendaylight.openflowplugin</groupId>
              <artifactId>openflowplugin-api</artifactId>
              <version>${openflowplugin.version}</version>
           </dependency>
          <dependency>
              <groupId>org.opendaylight.ovsdb</groupId>
              <artifactId>southbound-api</artifactId>
              <version>${ovsdb.version}</version>
          </dependency>
        <!-- end adding-->



## set required features


        <properties>
            ....
            <openflowplugin.version>0.2.4-Beryllium-SR4</openflowplugin.version>
            <ovsdb.version>1.2.3-Beryllium-SR2</ovsdb.version>
            ...
        </properties>

	<dependency>
           <groupId>org.opendaylight.openflowplugin</groupId>
           <artifactId>features-openflowplugin</artifactId>
           <classifier>features</classifier>
           <type>xml</type>
           <version>${openflowplugin.version}</version>
        </dependency>
	<dependency>
           <groupId>org.opendaylight.ovsdb</groupId>
           <artifactId>features-ovsdb</artifactId>
           <classifier>features</classifier>
           <type>xml</type>
           <version>${ovsdb.version}</version>
        </dependency>

