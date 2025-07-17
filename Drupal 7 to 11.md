<h2>D7 to D10/11 Migration Guide </h2>
<h4>Steps</h4>
<ol>
  <li>Analyze the D7 site deeply about their contents, their fields, taxonomies and all entities</li>
  <li>Find out all using contrib modules and write down in list</li>
  <li>Check compatiblities of modules in D10/11. and Add compatible versions in list of modules</li>
  <li>Set up a fresh D10/D11 site.[Since, db and configs of d7 and d10/11 is completely different]</li>
  <li>Add all required modules in composer.json with compatible version in your new d10/d11 site and run <b>Composer install</b> to install all required modules</li>
  <h5>Now Prepare for migration of contents and configuration</h5>
  <li>In settings.php of your D10/11 site, add this database migration config code to connect d7 to d10/11 site:
<code>
  $databases['migrate']['default'] = array (
  'driver' => 'mysql',
  'database' => 'drupal7_legacy',
  'username' => 'root',
  'password' => 'root',
  'host' => '127.0.0.1',
  'port' => '',
  'prefix' => '',
  'collation' => 'utf8mb4_general_ci',
);
</code>
    Add this below the existing database config of d10/11 database.
</li>
  <li>Now, Install these required modules for migration: <b>migrate, migrate_drupal, migrate_drupal_ui, migrate_upgrade,devel, migrate_devel</b> [Add all these in composer.json to install]</li>
  <li>Other useful modules worth install: <b>backup_migrate, pathauto, admin_toolbar, stage_file_proxy.</b> [Add all these in composer.json to install]</li>
  <li>enable all installed modules</li>
  <h5>Now, Start migration</h5>
  <li>Go to <b>/upgrade</b>, there you will get option to start migration, start your migration from there.</li>
  <li>Between migration, if there would be any error, fix it, clear Database and restart the migration</li>
</ol>
<h4>After all your d7 to d10/11 site migration done, then ensure all your configs and contents in your new site.<br/>Note: Views doesn't get migrated, so you need to manually create all view listings.</h4>
