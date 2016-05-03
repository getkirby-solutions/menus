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

- checkboxes just save a data value, not the page it self
- checkboxes field won't reflect page changes because they're separate entities
- changes like `uri`, `url`, won't be tracked
