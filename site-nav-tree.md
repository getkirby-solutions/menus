# Site navigation tree

Reference: nested menu: https://getkirby.com/docs/solutions/menus

```php
# template.php
<?php $pagesPrimary = $pages->visible(); ?>
<?php if($pagesPrimary->count()): ?>
	<nav>
		<ul class="list-unstyled">
			<!-- top pages -->
			<?php foreach($pagesPrimary as $pagePrimary): ?>
				<li class="margin-bottom-0">
					<a class="color-white border-0 transform-capitalize <?php e($pagePrimary->isOpen(), 'active ') ?>" href="<?php echo $pagePrimary->url() ?>">
						<?php echo $pagePrimary->title()->html(); ?>
					</a>
					<!-- pageSecondary pages -->
					<?php $pagesSecondary = $pagePrimary->pagesSecondary()->visible()->flip(); ?>
					<?php	 if($pagesSecondary->count()): ?>
						<ul class="list-unstyled" style="margin-left:0.3rem;">
							<?php $count = 1; ?>
							<?php foreach($pagesSecondary as $pageSecondary): ?>
								<li>
									<a class="color-muted border-0 <?php e($pagePrimary->isOpen(), ' active ') ?>" href="<?php echo $pageSecondary->url() ?>">
										<?php echo substr($pageSecondary->title(),0,25) . "…" ?>
									</a>
								</li>
								<?php if ($count > 2) { break; } else { $count++; } ?>
							<?php endforeach ?>
							<li>
								<a class="color-muted border-0 <?php e($pagePrimary->isOpen(), ' active ') ?>" href="<?php echo $pagePrimary->url() ?>">
									Ver más…
								</a>
							</li>
						</ul>
					<?php endif ?>
					<!-- end of pageSecondary -->
				</li>
			<?php endforeach ?>
			<!-- end of pagesPrimary -->
		</ul>
	</nav>
<?php endif ?>
```
