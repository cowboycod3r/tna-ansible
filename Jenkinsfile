stage 'init'
node {
    echo "do something init stuff"
}

stage 'test clean VM'
node {
    echo "test clean VM"
}

stage 'test existing VM'
node {
    echo "test existing VM"
}

stage 'deployment'
node {

    /* check out current state on the node */
    checkout scm

    /* Colorized Console Log */
    wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {

        /* execute ansible */
        ansiblePlaybook(playbook: 'site.yml', inventory: "/etc/ansible/hosts-${env.BRANCH_NAME}", colorized: true)
    }
}
