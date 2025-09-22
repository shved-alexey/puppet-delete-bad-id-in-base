# Foreman (puppet) delete bad host in base <br>

# We display a list of hosts from ID <br>
sudo -u postgres psql foreman -c 'select id, name, type, organization_id, location_id from hosts;' <br>

# We try to remove in Foreman-Rake Console <br>
foreman-rake console <br>
Host::Base.where(id: [XXX]).destroy_all <br>
  or <br>
Host.where(id: [233, 265, 274]).destroy_all <br>

# If an error, then we remove directly from the base
sudo -u postgres psql foreman -c "DELETE FROM host_puppet_facets WHERE host_id = XXX;" <br>
sudo -u postgres psql foreman -c "DELETE FROM host_facets_reported_data_facets WHERE host_id = XXX;" <br>

