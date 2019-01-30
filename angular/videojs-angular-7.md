**1. Adicionar dependência para video.js**

`
npm install video.js
`

**2. Adicionar dependências de scripts e styles ao projeto Angular**

No arquivo angular.json, adicionar aos estilos:  

`
"styles": [
  "./node_modules/video.js/dist/video-js.min.css",
  "src/styles.css"
]
`  
  
No arquivo angular.json, adicionar aos scripts:  
  
`
"scripts": [
  "./node_modules/video.js/dist/video.min.js"
]
`

**3. Adicionar vídeo no html do componente Angular**
  
```html
  <video #videoid id="id-ideo" class="video-js vjs-big-play-centered mini-play"
    width="640" height="360" style="margin: auto;">
    <source [src]="url" type="video/mp4">
  </video>
  
  <div>
  <button (click)="jumpTo(10)">10</button>
  <button (click)="jumpTo(20)">20</button>
  <button (click)="jumpTo(30)">30</button>
  <button (click)="jumpTo(40)">40</button>
  </div>
```

**4. Adicionar vídeo ao componente Angular**

```javascript
declare var videojs: any;

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent implements AfterViewInit {
  title = 'test-videojs';
  url = 'URL DO VIDEO';

  vidObj: any;
  
  @ViewChild('myvid') vid: ElementRef;

  ngAfterViewInit() {
    const options = {
      controls: true,
      autoplay: false,
      preload: 'auto',
      techOrder: ['html5']
    }    

    this.vidObj = new videojs(this.vid.nativeElement, options, function onPlayerReady() {});
  };

  public jumpTo(time: number): void {
    this.vidObj.currentTime(time)
  }
}
```
  
