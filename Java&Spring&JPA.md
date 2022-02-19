# 스프링 부트 & JPA 활용한 웹개발 공부

<br><br>

> ## domain 계층
주요 Annotation(어노테이션(@))
|Annotation|역할&사용|
|--|--|
|@Entity|JPA를 사용해서 테이블과 매핑할 클래스에 이용|
|@Table|name이라는 속성을 이용해 엔티티와 매핑할 테이블을 지정해주며 생략시 엔티티 이름 같은 이름의 테이블과 매핑|
|@Inheritance|
|@DiscriminatorColumn|
|@Getter, @Setter|각 속성의 getter와 setter을 만들어줌|
|@Id|key에 해당하는 속성에 이용|
|@GeneratedValue|
|@Column|컬럼과 매핑해주며 String형 같은 경우 기본값이 varchar(255)인데 length 속성을 이용하면 이 값을 변경할 수 있다.|
|@Embedded, @Embeddable|
|@OneToMany|
|@ManyToOne|
|@OneToOne|
|@JoinColumn|
|@Enumerated|enum 타입과 매핑해주며 되도록 value속성의 값을 EnumType.ORDINAL이 아닌 EumeType.String으로 사용한다.

<br><br>

> ## repository 계층
주요 Annotation(어노테이션(@))
|Annotation|역할&사용|
|--|--|
|@Repository|리포지토리 계층임을 표시
|@PersistenceContext|
|@RequiredArgsConstructor|

<br><br>

> ## service 계층
주요 Annotation(어노테이션(@))
|Annotation|역할&사용|
|--|--|
|@Service|서비스 계층임을 표시|
|@Transactional|
|@Autowired|
|@RequiredArgsConstructor|null값이면 안되는 속성의 값을 할당해주는 생성자|

<br><br>

> ## controller, web 계층
주요 Annotation(어노테이션(@))
|Annotation|역할&사용|
|--|--|
|@Controller|컨트롤러 계층임을 표시|
|@Slf4j|
|@RequiredArgsConstructor|null값이면 안되는 속성의 값을 할당해주는 생성자|
|@RequestMapping|
|@GetMapping|
|@PostMapping|
|@PathVariable|
|@ModelAttribute|
|@RequestParam|

<br><br>

> ## 테스트 코드
주요 Annotation(어노테이션(@))
|Annotation|역할&사용|
|--|--|
|@SpringBootTest|
|@Transactional|
|@Autowired|
|@Test|
