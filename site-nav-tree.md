# Site navigation tree

Reference: nested menu: https://getkirby.com/docs/solutions/menus

```php
# template.php
<?php $items = $pages->visible(); ?>
<?php if($items->count()): ?>
	<nav>
		<ul class="list-unstyled">
			<!-- top pages -->
			<?php foreach($items as $item): ?>
			<li class="margin-bottom-0">
				<a class="color-white border-0 transform-capitalize <?php e($item->isOpen(), ' active ') ?>" href="<?php echo $item->url() ?>">
					<?php echo $item->uri(); ?>
				</a>
				<!-- child pages -->
				<?php $children = $item->children()->visible()->flip(); ?>
				<?php	if($children->count() && false): ?>
					<ul class="list-unstyled" style="margin-left:0.3rem;">
						<?php $count = 1; ?>
						<?php foreach($children as $child): ?>
							<li>
								<svg class="color-muted icon"><use xlink:href="/packages/fontawesome/fontawesome.svg#icon-file-o"></use></svg>
								<a class="color-muted border-0 <?php e($item->isOpen(), ' active ') ?>" href="<?php echo $child->url() ?>">
									<?php echo substr($child->title(),0,25) . "…" ?>
								</a>
							</li>
							<?php if ($count > 2) { break; } else { $count++; } ?>
						<?php endforeach ?>
						<li>
							<svg class="color-muted icon"><use xlink:href="/packages/fontawesome/fontawesome.svg#icon-file-o"></use></svg>
							<a class="color-muted border-0 <?php e($item->isOpen(), ' active ') ?>" href="<?php echo $item->url() ?>">
								Ver más…
							</a>
						</li>
					</ul>
				<?php endif ?>
				<!-- end of child pages -->
			</li>
			<?php endforeach ?>
			<!-- end of top pages -->
		</ul>
	</nav>
<?php endif ?>

```
