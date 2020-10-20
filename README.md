# CKAD_Preparation
Repository with some reference information about the exam, tips &amp; tricks and Reference URLs.

CKAD is a hands-on exam provided by CNCF (Cloud Native Computing Foundation). You can get all the general details of this exam here:
https://www.cncf.io/certification/ckad/

There are many forums and guidelines on this exam, I will try to explain the preparation I went through and some key details I found while taking the exam.

# 1. Preparation & Tips
  - Preparation for this exam, difference to many people may think, is not only about how fast you execute the commands. Instead, you must know where to look for and what is the best approach to solve a issue. For that, a solid Theory of the following concepts is important:
    - Ingress Controllers
    - Services
    - SideCar Containers
    - Volumes and VolumeClaims
    - Network Policies
    - Service Account
  - Time is your best ally and your worst enemy for this exam, so be aware of it. In contrast to regular Pearson exams, this exam does not have a digital countdown   timer, but instead a green bar that will decrease it's size as the times goes by. Don't get nervous and stick to your plan. 
  - NO questions should demand you more than 5 minutes. If that happens, just move on and mark it for a later review. Keep in mind that 60% is the minimum score and you must achieve that score with confidence. 
  - Every second you save is priceless, that is why I suggest the following aliases (run them as soon the exam starts, and get familiar with this syntaxis before-hand).
    - alias k=kubectl
    - alias kg="kubectl get"
    - alias ke="kubectl explain" (super important when a typo error is blocking your way to the glory!)
    - alias kd="kubectl describe"
    - alias kdel="kubectl delete"
    - alias ka="kubectl apply -f "
    - alias kn="kubectl config set-context --current --namespace" (use this with extreme caution, changing namespaces during exam means you need to return to default ns for every single question).
  - A hands-on exam like this one demands a high confidence in imperative commands and Linux, so be sure you are prepared to do some basic parsing operations, remote SSH connections, sudo commands, edit yaml files on the go and use vim/nano/vi text editor in Linux easily.
  - I mention in the previous bullet about imperative commands. The following commands I used the most during my preparation & exam:
    - Generate POD Manifest YAML file (-o yaml). Don't create it(--dry-run)
        - kubectl run nginx --image=nginx --restart=Never --dry-run -o yaml
    - Create a deployment
        - kubectl create deployment --image=nginx nginx
    - Generate Deployment YAML file (-o yaml). Don't create it(--dry-run):
        - kubectl create deployment --image=nginx nginx --dry-run -o yaml
    - Save it to a file - (If you need to modify or add some other details):
        - kubectl create deployment --image=nginx nginx --dry-run -o yaml > nginx-deployment.yaml
    - Create a Service named redis-service of type ClusterIP to expose pod redis on port 6379:
        - kubectl expose pod redis --port=6379 --name redis-service --dry-run -o yaml
    - Create a Service named nginx of type NodePort to expose pod nginx's port 80 on port 30080 on the nodes:
        - kubectl expose pod nginx --port=80 --name nginx-service --dry-run -o yaml
    - Create Secrets:
        - k create secret generic <secret-name> --from-literal=<key>=<value>
        - k create secrete generic <secret-name> --from-file=<path-to-file>
  - For preparation, in addition to different online courses in the market, you can follow different Kubernetes guides in you own Kubernetes Cluster:
  
    - Creating Google Cloud Kubernetes cluster:
        - gcloud config set project [Name]
        - gcloud config set compute/zone [Zone]
        - gcloud container clusters create kuboperu --num-nodes=[Number of initial nodes]

# 2 Reference Links
  
   - Practice Links:
     - https://github.com/dgkanatsios/CKAD-exercises
     - https://github.com/twajr/ckad-prep-notes#tasks-from-kubernetes-doc
     
   - Useful Tips & Tricks:
     - https://github.com/saaguero/ckad-notes/#my-experience-and-tips
     - https://github.com/twajr/ckad-prep-notes#tips
   
   - Reference from other previous experiences:
     - https://codeburst.io/kubernetes-ckad-weekly-challenges-overview-and-tips-7282b36a2681
     - https://medium.com/chotot/tips-tricks-to-pass-certified-kubernetes-application-developer-ckad-exam-67c9e1b32e6e
     - https://medium.com/@alexellisuk/kubernetes-1-18-broke-kubectl-run-heres-what-to-do-about-it-2a88e5fb389a



    
