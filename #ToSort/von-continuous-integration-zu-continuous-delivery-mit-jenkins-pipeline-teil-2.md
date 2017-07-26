# Von Continuous Integration zu Continuous Delivery mit Jenkins Pipeline – Teil 2

_Captured: 2017-02-05 at 13:39 from [www.informatik-aktuell.de](https://www.informatik-aktuell.de/entwicklung/methoden/von-continuous-integration-zu-continuous-delivery-mit-jenkins-pipeline-teil-2.html)_

![© Jenkins logo with title von The Jenkins project. Lizenziert unter © Jenkins logo with title von The Jenkins project. Lizenziert unter Wikimedia Commons](https://www.informatik-aktuell.de/fileadmin/_processed_/csm_720-Jenkins_13882ad843.jpg)

> _(C) Jenkins logo with title von The Jenkins project. Lizenziert unter Wikimedia Commons_

**Dies ist der zweite Teil uber Continuous Delivery. Im ersten Teil "[Von Continuous Integration zu Continuous Delivery mit Jenkins Workflow](https://www.informatik-aktuell.de/entwicklung/methoden/von-continuous-integration-zu-continuous-delivery-mit-jenkins-workflow.html)" habe ich uber Jenkins Workflow gesprochen. Kurzlich wurde Jenkins Workflow in Jenkins Pipeline umbenannt. Also werde ich in diesem Teil uber Jenkins Pipeline sprechen, gemeint ist jeweils dasselbe. **

**Der erste Teil endete mit einem einfachen Build Pipeline Job, der ein bestimmtes Stuck Software von der Entwicklung bis in die Produktion transportiert. Was also kommt danach?**

**Hat man mehrere dieser Build Pipelines, wird sich der Code dieser Pipelines uberschneiden. Der nachste logische Schritt wird also sein, diese Gemeinsamkeiten an einer Stelle zusammenzuziehen. Das ist schon aus Grunden der Wartbarkeit und Erweiterbarkeit wichtig, die Informatik kennt hierfur Begriffe wie "DRY" (Don't Repeat Yourself ****[[1]](https://www.informatik-aktuell.de/entwicklung/methoden/von-continuous-integration-zu-continuous-delivery-mit-jenkins-pipeline-teil-2.html)****) und "Single Point of Truth"****.**

**Es gibt mehrere Moglichkeiten der Implementierung und man kann sie sogar fur maximalen Nutzen miteinander kombinieren.**

## Templates

Die variablen Teile des Build Pipeline Codes werden als Parameter des Templates formuliert. Das Build Pipeline Skript sieht dem Skript aus dem ersten Teil sehr ahnlich, nur die variablen Teile folgen einer anderen Syntax (hervorgehoben in rot):
    
    
    def String jenkinsTestHost = "localhost:8080/"  
    def String jenkinsProductionHost = "localhost:8081/"  
    def String stashBaseName = "plugin"  
      
    stage "Build"  
    node {  
    	git url:pluginSource  
      
    	def mvnHome = tool 'M3'  
    	// we will come back to the tests later on  
    	sh "${mvnHome}/bin/mvn -B -DskipTests=true install"   
      
    	stash name: stashBaseName+”-plugin”, includes: "target/${pluginFile}"  
    	stash name: stashBaseName+"-sources", excludes: "target/*"  
      
    	}  
    checkpoint "plugin binary is built"  
      
    stage "Integration Tests and Quality Metrics"  
    parallel  
    	"Integration Tests": {  
    		node {  
    			echo "++++++++++ Integration Tests ++++++++++"  
    			// we need to get the source again just in case we are running on a different node  
    			unstash stashBaseName+"-sources"   
    			def mvnHome = tool 'M3'  
    			sh "${mvnHome}/bin/mvn integration-test"  
    			}  
    		},  
    "Quality Metrics": {  
    	node {  
    		echo "++++++++++ Quality Metrics ++++++++++"  
    		// we need to get the source again just in case we are running on a different node  
    		unstash stashBaseName+"-sources"   
    		def mvnHome = tool 'M3'  
    		sh "${mvnHome}/bin/mvn sonar:sonar"  
    		}  
    	}  
      
    // check that the clients still can work with the host  
    // we might want to limit the concurrency here because of resource limits  
    stage name: "Load Tests", concurrency: 1  
    	parallel  
    		"load test #1" : {	  
    			node {  
     		  
    				executeLoadTest(jenkinsTestHost)  
    		}  
    		},  
    		"load test #2": {  
     	  
    			node {  
    				executeLoadTest(jenkinsTestHost)  
    		}  
    		},  
     	  
    		"load test #3": {  
     	  
    		node {  
     		  
    			executeLoadTest(jenkinsTestHost)  
    		}  
    		}  
    checkpoint "all tests are done"   
      
    stage "Deploy to Production"  
    node {  
    	input "All tests are ok. Shall we continue to deploy into production (This will initiate a Jenkins restart) ?"  
    	unstash stashBaseName+"-plugin"   
    	uploadPluginAndRestartJenkins ( jenkinsProductionHost, "pluginFile" )  
    	}

Das ist schon mal gar nicht so schlecht, aber zunachst konnen wir einzelne Teile noch in Methoden auslagern. Beispielsweise wie folgt:
    
    
    def mvnInstall ( ) {  
    	def mvnHome = tool 'M3'  
    	// we will come back to the tests later on  
    	sh "${mvnHome}/bin/mvn -B -DskipTests=true install"   
    }

dann sahe die Build Stage wie folgt aus:
    
    
    stage "Build"  
    node {  
    	git url:pluginSource  
      
    	mvnInstall()   
      
    	stash name: stashBaseName+”-plugin”, includes: "target/${pluginFile}"  
    	stash name: stashBaseName+"-sources", excludes: "target/*"  
      
    	}  
    checkpoint "plugin binary is built"

Oder noch etwas konsequenter sogar so:
    
    
    def buildStage ( String pluginSource, String pluginFile ) {  
    	git url:pluginSource  
      
    	mvnInstall()  
      
    	stash name: stashBaseName+”-plugin”, includes: "target/${pluginFile}"  
    	stash name: stashBaseName+"-sources", excludes: "target/*"  
    }

Dann sahe die Stage wie folgt aus:
    
    
    stage "Build"  
    node {  
    	buildStage(pluginSource,pluginFile)  
    	}  
    checkpoint "plugin binary is built"

Wenden wir das konsequent auf die gesamte Build Pipeline an, bekommen wir folgendes:
    
    
    def String jenkinsTestHost = "localhost:8080/"  
    def String jenkinsProductionHost = "localhost:8081/"  
    def String stashBaseName = "plugin"  
      
    stage "Build"  
    node {  
    	buildStage(pluginSource,pluginFile)  
    	}  
    checkpoint "plugin binary is built"  
      
    stage "Integration Tests and Quality Metrics"  
    parallel  
    	"Integration Tests": {  
    		node {  
    			integrationTest()  
    			}  
    		},  
    	"Quality Metrics": {  
    		node {  
    			qualityMetrics()  
    			}  
    		}  
      
    // check that the clients still can work with the host  
    // we might want to limit the concurrency here because of resource limits  
    stage name: "Load Tests", concurrency: 1  
    	  
    	parallel  
    		"load test #1" : {  
    			node {  
    				executeLoadTest(jenkinsTestHost)  
    		}  
    		},  
    		"load test #2": {  
     	  
    			node {  
     		  
    				executeLoadTest(jenkinsTestHost)  
    		}  
    		},  
     	  
    		"load test #3": {  
     	  
    		node {  
     		  
    				executeLoadTest(jenkinsTestHost)  
    		}  
    		}  
    checkpoint "all tests are done"   
      
    stage "Deploy to Production"  
    node {  
    deployToProduction(pluginFile)  
      
    }

Damit haben wir jetzt eine Status erreicht, wo sowohl Development als auch QA als auch Operations uber die Build Pipeline reden konnen, ohne sich in Details zu verlieren.

Und wohin mit den ganzen schonen Methoden, die wir gerade extrahiert haben? Auch dafur gibt es naturlich einen Platz:

## Pipeline Global Library

Repository fur Methoden und Variablen, die innerhalb einer Organization potentiell von allen Build Pipelines gebraucht werden konnen.

Vereinfacht gesagt, nehmen wir alle diese Methoden - sofern es fur mehr als eine Build Pipeline Sinn macht - und speichern sie an einer zentralen Stelle. Eine Pipeline Global Library hat eine sehr einfache Struktur:
    
    
    (root)  
     +- src                     # groovy source files  
     |   +- org  
     |       +- foo  
     |           +- Bar.groovy  # for org.foo.Bar class  
     +- vars  
         +- foo.groovy          # for global 'foo' variable/function  
         +- foo.txt             # help for 'foo' variable/function

Alle in der Global Library definierten Methoden und Variablen sind "automagisch" fur jedes Build Pipeline Script zugreifbar.

## Fazit

![Abb.1: Visualisierung. © Bernhard Cygan](https://www.informatik-aktuell.de/fileadmin/_processed_/csm_Visualisierung_abb1_cygan_63bf1f5725.jpg)

> _Abb.1: Visualisierung. (C) Bernhard Cygan_

Und der Lohn all dieser Muhen? In der Visualisierung sieht alles immer noch genauso aus wie vorher (s. Abb.1).

Vielleicht ein wenig enttauschend nach der ganzen Arbeit. Aber wenn wir weitere - mehr oder weniger gleichartige - Module bauen wollen, verfugen wir jetzt uber einen gut ausgestatteten Werkzeugkasten, der uns das Erstellen und Warten der nachsten Build Pipelines deutlich erleichtert.

Mit diesen Methoden und Hilfsmitteln ist es moglich, eine Build Pipeline zu definieren, zu warten und zu erweitern, die von allen Beteiligten einer DevOps-Organisation verstanden wird. Ganz nebenbei haben wir einige wichtige Prinzipien der Softwareentwicklung auf Build Pipeline Skripts angewandt.
