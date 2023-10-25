#java #spring #sse

SSEs happen via HTTP protocol where client establishes a connection and subscribes to an event source on the server.
# How to send SSEs from Spring WebApp ?
``` Java
@GetMapping("/stream-data")  
public SseEmitter getStreamData() {  
  SseEmitter emitter = new SseEmitter();  
  
  ExecutorService executorService = Executors.newSingleThreadExecutor();  
  executorService.execute(() -> {  
    try {  
      for (int i = 0;i < 10;i++) {  
        var eventData = new EventData();  
        eventData.setId(UUID.randomUUID().toString());  
        eventData.setName("Hola");  
  
        SseEmitter.SseEventBuilder event = SseEmitter.event()  
            .data(eventData);  
        emitter.send(event);  
  
        Thread.sleep(2000);  
      }    } catch (Exception ignored) {}  
  });  
  return emitter;  
}
```

The **EventData** class is:
``` Java
public class EventData {  
  private String name;  
  private String id;  
  
  public String getId() {  
    return id;  
  }  
  public String getName() {  
    return name;  
  }  
  public void setId(String id) {  
    this.id = id;  
  }  
  public void setName(String name) {  
    this.name = name;  
  }
}
```

This can be tested via **postman** or via a vanilla jsCode.
``` js
const url = "http://localhost:8080/stream-data";
const eventSource = new EventSource(url);

eventSource.onmessage = (event) => {
	const data =JSON.parse(event.data);
	const body = document.getElementById("id1");
	if (body == null) {
		return;
	}
	
	const childDiv = document.createElement("div");
	childDiv.innerHTML = `${event.data}`;
	body.appendChild(childDiv);
};

eventSource.onerror = (error) => {
	console.log(error);
	eventSource.close();
};
```