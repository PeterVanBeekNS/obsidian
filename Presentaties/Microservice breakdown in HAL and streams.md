- **Aanleiding**:    
    - Geboren uit vraag naar berichten per seconde voor orbid aed.
    - Implementatie van best practices.
    - 
- **Voorstel**:    
    - Opsplitsen van treinzijde microservice.
    - Twee nieuwe microservices: HAL en Streams.
    - 
- **HAL Microservice**:    
    - Specifiek per treintype.
    - Hardware-interacties en abstractie.
    - Uniforme uitgaande gegevensstromen.
- **Streams Microservice**:    
     - Microservice voor bestaande events
     - Microservice voor berichten per seconde
     
- **Externe Communicatie**:    
    - AMQP broker voor abonnementen.
    
- **Voordelen**:    
    - Schaalbaarheid: modulaire uitbreiding.
    - Flexibiliteit: aanpassing per treintype.
    - Efficiëntie: geoptimaliseerd middelengebruik.
    - Robuustheid: betrouwbare communicatie.
    - Configuratiebeheer: eenvoudige updates.
    
- **Investering en Rendement**:
	- Initiële inspanning vereist voor implementatie.
	- Langetermijnvoordelen door verbeterde efficiëntie en verminderde complexiteit.
	- Toekomstige tijdsbesparing en kostenreductie dankzij eenvoudiger uitbreidingen en onderhoud