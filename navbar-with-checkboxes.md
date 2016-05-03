# Navigation from panel checkboxes

Panel checkboxes

```yaml
menu_primary:
  label: Show on top bar
  type: checkboxes
  options: children
```

Checkboxes return a string

```php
# template
<?php foreach ($site->menu_primary()->split() as $item): ?>
	<li>
		<a class="transform-capitalize" href="<?php echo $pages->find($item)->url() ?>">
			<?php echo $pages->find($item)->uri() ?>
		</a>
	</li>
<?php endforeach; ?>
```
