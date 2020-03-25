# fastify-gm
Fastify plugin for GraphicsMagick.

# Installation
```
npm i https://github.com/wwwins/fastify-gm.git --save
```

# Usage
```
fastify.register(require('fastify-gm'), {
  font: path.join(__dirname, '../fonts/NotoSansTC-Regular.otf'),
  from_folder: path.join(__dirname, '../public/images/'),
  to_folder: path.join(__dirname, '../public/upload/'),
});

fastify.get('/jpg/:color/:text', async (req, res) => {
  const text = req.params.text;
  const color = req.params.color;
  const uid = uuid();
  if (text) {
    await fastify.textOverImage({text:text, pos:{x:50,y:150}, color:color, fileId:uid, bgName:'xxx.jpg'});
    return { success: true, jpg: API_HOST+'/upload/'+uid+'.jpg' }
  }
})
```
