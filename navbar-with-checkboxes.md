# Navigation from panel checkboxes

Site blueprint

```yaml
# site.yml
menu_primary:
  label: Show on top bar
  type: checkboxes
  options: children
```

Template

```php
# Checkboxes return a string
<?php foreach ($site->menu_primary()->split() as $item): ?>
	<li>
		<a class="transform-capitalize" href="<?php echo $pages->find($item)->url() ?>">
			<?php echo $pages->find($item)->uri() ?>
		</a>
	</li>
<?php endforeach; ?>
```

Issues:

- `site.yml` won't fetch page changes, they're separate entities
