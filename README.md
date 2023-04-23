# pdmount-vm-tf-gcp-
  resource "google_compute_instance" "vm" {
  name = "kdtf"
  zone = "europe-north1-a"
  machine_type = "e2-micro"
 
 boot_disk {
    initialize_params {
       image = "debian-cloud/debian-11"
       }
    }

   metadata_startup_script = "sudo su;  sudo mkfs.ext4 -m 0 -E lazy_itable_init=0,lazy_journal_init=0,discard /dev/sdb ; sudo mkdir -p /mnt/disks/kd ;sudo mount -o discard,defaults /dev/sdb /mnt/disks/kd ; cd /var/log ; cp -r /var/log/chrony /mnt/disks/kd ; apt update; apt install nfs-common -y; mkdir kd1 "


network_interface {

    network = "default"

    access_config {

      }
     }
    }
