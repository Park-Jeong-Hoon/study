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
|@Getter, @Setter|
|@Id|
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
|@Repository|
|@PersistenceContext|
|@RequiredArgsConstructor|

<br><br>

> ## service 계층
주요 Annotation(어노테이션(@))
|Annotation|역할&사용|
|--|--|
|@Service|
|@Transactional|
|@Autowired|
|@RequiredArgsConstructor|

<br><br>

> ## controller, web 계층
주요 Annotation(어노테이션(@))
|Annotation|역할&사용|
|--|--|
|@Controller|
|@Slf4j|
|@RequiredArgsConstructor|
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
