pipeline {
 parameters {
         string(name: 'yaml_value', defaultValue: 'repo.yaml')
  }
    agent any
         stages{
           
           stage('Read YAML file') {
             steps {
               script{ 
                  // datas = readYaml (file: 'repo.yaml') 
                   //echo "ymlfile value $yaml_value"
                   datas = readYaml (file: "${env.yaml_value}")                    
                             
                   if(datas.services.myagent1.version.toString().endsWith(".0.0"))
                    createBranch(datas.services.myagent1.repo.toString(),datas.services.myagent1.version.toString())
					
                   else
                    createTag(datas.services.myagent1.repo.toString(),datas.services.myagent1.version.toString())
                   
                    if(datas.services.myagent2.version.toString().endsWith(".0.0"))
					createBranch(datas.services.myagent2.repo.toString(),datas.services.myagent2.version.toString())
                    
                   else
				   createTag(datas.services.myagent2.repo.toString(),datas.services.myagent2.version.toString())
                    
                                   
                 }  
              }
           }
         }
}

def createBranch(String repo, String version){
   echo "inside createBranch method and repo is "+ repo + " version is "+version               
            
           sh label: '', script: '''
           mkdir test'''
          //  sh "git clone http://chaitanya-Inspiron-5521/csenapati12/gittag.git"
           
}

def createTag(String repo, String version){     
     echo "inside createTag method and repo is "+ repo + " version is "+version  
     sh label: '', script: '''
     mkdir test'''
     sh "git clone http://chaitanya-Inspiron-5521/csenapati12/gittag.git"
           
          
}
