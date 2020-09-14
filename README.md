anthos-environ-samples
==================================================

# NAME

  anthos-environ-samples

# SYNOPSIS

  Get and instantiate package on Day 1:
    
    $ kpt pkg get git@github.com:phanimarupaka/anthos-sse-end-state.git ./
    $ cd anthos-sse-end-state
    $ kpt cfg tree .

    // list-setters will recursively list setters in subpackages
    $ kpt cfg list-setters .
    
    // Set all the setter parameters. Can be dummy values for demo.

   Add more clusters and extend the membership on Day n:
    
    $ kpt pkg get git@github.com:phanimarupaka/anthos-sse-end-state.git/gke-cluster-1 gke-cluster-2
    
    $ kpt cfg set gke-cluster-2 gcloud.container.cluster.name gke-cluster-2
    $ kpt cfg set gke-cluster-2 gcloud.container.nodepool.name us-nodepool-2
    
    // Run the set command on all the subpackages with -R flag
    // only the packages with the setter will be set
    $ kpt cfg set . membership gke-cluster-1 gke-cluster-2 -R
    ./
    setter "membership" is not found
    
    cloud-run/
    set 1 field(s)
    
    config-management/
    set 1 field(s)
    
    gke-cluster-1/
    setter "membership" is not found
    
    gke-cluster-2/
    setter "membership" is not found
    
    service-mesh/
    set 1 field(s)
    

