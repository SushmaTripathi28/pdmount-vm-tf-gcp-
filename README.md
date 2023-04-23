# pdmount-vm-tf-gcp-
resource "google_compute_instance" "demotf" {
  name = var.vm_name
  machine_type = var.vm_machine
  zone = var.vm_zone

  boot_disk {
    initialize_params{
      image = var.vm_image
    }
  }

network_interface {
  network = google_compute_network.network.name
  subnetwork = google_compute_subnetwork.subnet.name
  access_config{

  }
}
}
