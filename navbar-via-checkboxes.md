# Navigation via checkboxes

Site blueprint

```yaml
# site.yml
menuPrimary:
menuPrimary:
  label: Menu
  type: checkboxes
  options: query
  query:
    page: /
    fetch: children
    value: '{{hash}}'
    text: '{{title}}'
```

Template

```php
# checkboxes field returns string, split() converts string into array
<?php if ($site->menuPrimary()->isNotEmpty()): ?>
  <ul class="<?php echo $listClass ?>">
    <?php if ($menuHashes = $site->menuPrimary()->split()): ?>
      <?php foreach($menuHashes as $menuItemHash): ?>
        <?php $menuPage = $pages->findBy('hash', $menuItemHash); ?>
        <?php if ($menuPage->isVisible()): ?>
          <li class="<?php echo $itemClass ?>">
            <a class="<?php echo $linkClass ?>" href="<?php echo $menuPage->url(); ?>">
              <?php echo $menuPage->title(); ?>
            </a>
          </li>
        <?php endif; ?>
      <?php endforeach; ?>
    <?php endif; ?>
  </ul>
<?php endif; ?>

```

Issues:

- checkboxes field won't reflect page changes
- changes like `uri`, `url`, won't be tracked
