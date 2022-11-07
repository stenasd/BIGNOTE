const actorNameSuffix = "_cloned";

canvas.tokens.controlled.forEach(o => {
  Actor.create(o.actor).then(a => {
    a.update({name: a.name + actorNameSuffix});
  });
});