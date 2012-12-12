fungibility
===========

http://blog.fungibleclouds.com/blog/2012/12/09/using-chef-to-deploy-cloud-applications/

Caution:

The git repo does not preserve a hack that was described in the blog post. That hack requires manually patching the mysql community cookbook by adding this segment on the very top.

    # Customization: get passwords from encrypted data bag
    secrets = Chef::EncryptedDataBagItem.load("secrets", "mysql")
    if secrets && mysql_passwords = secrets[node.chef_environment] 
      node['mysql']['server_root_password'] = mysql_passwords['root']
      node['mysql']['server_debian_password'] = mysql_passwords['debian']
      node['mysql']['server_repl_password'] = mysql_passwords['repl']
    end

