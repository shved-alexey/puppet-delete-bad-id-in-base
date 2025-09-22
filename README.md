# Foreman (puppet) delete bad host in base

# We display a list of hosts from ID
sudo -u postgres psql foreman -c 'select id, name, type, organization_id, location_id from hosts;'

# We try to remove in Foreman-Rake Console
foreman-rake console
Host::Base.where(id: [XXX]).destroy_all
  or
Host.where(id: [233, 265, 274]).destroy_all

# If an error, then we remove directly from the base
sudo -u postgres psql foreman -c "DELETE FROM host_puppet_facets WHERE host_id = XXX;"
sudo -u postgres psql foreman -c "DELETE FROM host_facets_reported_data_facets WHERE host_id = XXX;"

