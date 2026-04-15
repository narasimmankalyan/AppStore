        pipeline{
            agent any

            environment{
                DOCKERHUB_CREDIENTAILS=credentials("dockerhub")
            }

            parameters{
                string(name: "Environment",defaultValue:"dev",description:"make deployment after what should happen")
                choice(name:"Selection",choices:["build","test"],description:"select the action you want to perform")
                booleanParam(name:"continue",defaultValue:false,description:"weather you want to continue or not ")
            }
            stages{
                stage("First_stage"){
                    steps{
                        script{
                            if(params.Environment=="dev"){
                                println("First_stage_of_scripts")
                            }
                            println(test())
                        }
 
                }
                }
                stage("Docker-Login"){
                    steps{
                    sh """
                    echo "---------------Loging to docker hub-----------"
                    docker login -u $DOCKERHUB_CREDIENTAILS_usr -p $DOCKERHUB_CREDIENTAILS_PSW
                    echo "---------------Successfully log in to docker hub-----------"
                    """
                }
                }


            }
        }
def test(){
    return "______final_value______"
}
