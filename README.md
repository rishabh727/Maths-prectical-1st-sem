<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE Machine [
<!ELEMENT Machine (PunctChar*, Field*, FileChannel*, Register*, RegisterArray*, ConditionBit*, RAM*, Set*, Test*, Increment*, Shift*, Logical*, Arithmetic*, Branch*, TransferRtoR*, TransferRtoA*, TransferAtoR*, Decode*, SetCondBit*, IO*, MemoryAccess*, End, Comment*, EQU*, FetchSequence, MachineInstruction*, HighlightingInfo?, LoadingInfo?, IndexingInfo?, ProgramCounterInfo?, ModuleWindowsInfo?) >
<!ATTLIST Machine name CDATA "unnamed">
<!ELEMENT PunctChar EMPTY>
<!ATTLIST PunctChar char CDATA #REQUIRED use  (symbol|token|label|comment|pseudo|illegal) #REQUIRED>
<!ELEMENT Field (FieldValue*)>
<!ATTLIST Field name CDATA #REQUIRED type  (required|optional|ignored) #REQUIRED numBits CDATA #REQUIRED relativity (absolute|pcRelativePreIncr|pcRelativePostIncr) #REQUIRED defaultValue CDATA #REQUIRED signed (true|false) #REQUIRED id ID #REQUIRED>
<!ELEMENT FieldValue EMPTY>
<!ATTLIST FieldValue name CDATA #REQUIRED value CDATA #REQUIRED>
<!ELEMENT FileChannel EMPTY>
<!ATTLIST FileChannel file CDATA #REQUIRED id CDATA #REQUIRED>
<!ELEMENT Register EMPTY>
<!ATTLIST Register name CDATA #REQUIRED width CDATA #REQUIRED initialValue CDATA #REQUIRED readOnly (true|false) "false" id ID #REQUIRED>
<!ELEMENT RegisterArray (Register+)>
<!ATTLIST RegisterArray name CDATA #REQUIRED width CDATA #REQUIRED length CDATA #REQUIRED id ID #REQUIRED>
<!ELEMENT ConditionBit EMPTY>
<!ATTLIST ConditionBit name CDATA #REQUIRED bit CDATA #REQUIRED register IDREF #REQUIRED halt (true|false) "false" id ID #REQUIRED>
<!ELEMENT RAM EMPTY>
<!ATTLIST RAM name CDATA #REQUIRED length CDATA #REQUIRED id ID #REQUIRED cellSize CDATA "8">
<!ELEMENT Increment EMPTY>
<!ATTLIST Increment name CDATA #REQUIRED register IDREF #REQUIRED overflowBit IDREF #IMPLIED carryBit IDREF #IMPLIED delta CDATA #REQUIRED id ID #REQUIRED>
<!ELEMENT Arithmetic EMPTY>
<!ATTLIST Arithmetic name CDATA #REQUIRED type (ADD|SUBTRACT|MULTIPLY|DIVIDE) #REQUIRED source1 IDREF #REQUIRED source2 IDREF #REQUIRED destination IDREF #REQUIRED overflowBit IDREF #IMPLIED  carryBit IDREF #IMPLIED  id ID #REQUIRED>
<!ELEMENT TransferRtoR EMPTY>
<!ATTLIST TransferRtoR name CDATA #REQUIRED source IDREF #REQUIRED srcStartBit CDATA #REQUIRED dest IDREF #REQUIRED destStartBit CDATA #REQUIRED numBits CDATA #REQUIRED id ID #REQUIRED>
<!ELEMENT TransferRtoA EMPTY>
<!ATTLIST TransferRtoA name CDATA #REQUIRED source IDREF #REQUIRED srcStartBit CDATA #REQUIRED dest IDREF #REQUIRED destStartBit CDATA #REQUIRED numBits CDATA #REQUIRED index IDREF #REQUIRED indexStart CDATA #IMPLIED indexNumBits CDATA #IMPLIED id ID #REQUIRED>
<!ELEMENT TransferAtoR EMPTY>
<!ATTLIST TransferAtoR name CDATA #REQUIRED source IDREF #REQUIRED srcStartBit CDATA #REQUIRED dest IDREF #REQUIRED destStartBit CDATA #REQUIRED numBits CDATA #REQUIRED index IDREF #REQUIRED indexStart CDATA #IMPLIED indexNumBits CDATA #IMPLIED id ID #REQUIRED>
<!ELEMENT Shift EMPTY>
<!ATTLIST Shift name CDATA #REQUIRED source IDREF #REQUIRED destination IDREF #REQUIRED type (logical | arithmetic | cyclic) #REQUIRED direction (right | left) #REQUIRED distance CDATA #REQUIRED id ID #REQUIRED>
<!ELEMENT Branch EMPTY>
<!ATTLIST Branch name CDATA #REQUIRED amount CDATA #REQUIRED id ID #REQUIRED>
<!ELEMENT Logical EMPTY>
<!ATTLIST Logical name CDATA #REQUIRED source1 IDREF #REQUIRED source2 IDREF #REQUIRED destination IDREF #REQUIRED type (AND | OR | NAND | NOR | XOR | NOT) #REQUIRED id ID #REQUIRED>
<!ELEMENT Set EMPTY>
<!ATTLIST Set name CDATA #REQUIRED register IDREF #REQUIRED start CDATA #REQUIRED numBits CDATA #REQUIRED value CDATA #REQUIRED id ID #REQUIRED>
<!ELEMENT Test EMPTY >
<!ATTLIST Test name CDATA #REQUIRED register IDREF #REQUIRED start CDATA #REQUIRED numBits CDATA #REQUIRED comparison (EQ | NE | LT | GT | LE | GE ) #REQUIRED value CDATA #REQUIRED omission CDATA #REQUIRED id ID #REQUIRED>
<!ELEMENT Decode EMPTY >
<!ATTLIST Decode name CDATA #REQUIRED ir IDREF #REQUIRED id ID #REQUIRED>
<!ELEMENT IO EMPTY >
<!ATTLIST IO name CDATA #REQUIRED direction (input | output) #REQUIRED type (integer | ascii | unicode) #REQUIRED buffer IDREF #REQUIRED connection CDATA #IMPLIED id ID #REQUIRED>
<!ELEMENT MemoryAccess EMPTY >
<!ATTLIST MemoryAccess name CDATA #REQUIRED direction (read | write ) #REQUIRED memory IDREF #REQUIRED data IDREF #REQUIRED address IDREF #REQUIRED id ID #REQUIRED>
<!ELEMENT SetCondBit EMPTY >
<!ATTLIST SetCondBit name CDATA #REQUIRED bit IDREF #REQUIRED value (0 | 1) #REQUIRED id ID #REQUIRED>
<!ELEMENT End EMPTY>
<!ATTLIST End id ID #REQUIRED>
<!ELEMENT Comment EMPTY>
<!ATTLIST Comment name CDATA #REQUIRED id ID #REQUIRED>
<!ELEMENT Microinstruction EMPTY>
<!ATTLIST Microinstruction microRef IDREF #REQUIRED>
<!ELEMENT MachineInstruction (Microinstruction*)>
<!ATTLIST MachineInstruction name CDATA #REQUIRED opcode CDATA #REQUIRED instructionFormat CDATA #REQUIRED assemblyFormat CDATA #REQUIRED instructionColors CDATA #REQUIRED assemblyColors CDATA #REQUIRED>
<!ELEMENT FetchSequence (Microinstruction*) >
<!ELEMENT EQU EMPTY>
<!ATTLIST EQU name CDATA #REQUIRED value CDATA #REQUIRED>
<!ELEMENT HighlightingInfo (RegisterRAMPair*)>
<!ELEMENT RegisterRAMPair EMPTY>
<!ATTLIST RegisterRAMPair register IDREF #REQUIRED ram IDREF #REQUIRED dynamic (true|false) #REQUIRED>
<!ELEMENT LoadingInfo EMPTY>
<!ATTLIST LoadingInfo ram IDREF #IMPLIED startingAddress CDATA "0">
<!ELEMENT IndexingInfo EMPTY>
<!ATTLIST IndexingInfo indexFromRight CDATA "false">
<!ELEMENT ProgramCounterInfo EMPTY>
<!ATTLIST ProgramCounterInfo programCounter IDREF #REQUIRED>
<!ELEMENT ModuleWindowsInfo ((RegisterWindowInfo | RegisterArrayWindowInfo | RAMWindowInfo)*) >
<!ELEMENT RegisterWindowInfo EMPTY>
<!ATTLIST RegisterWindowInfo top CDATA "50" left CDATA "50" width CDATA "300" height CDATA "150" base (Decimal|Binary|Hexadecimal|Ascii|UnsignedDec|Unicode)  "Decimal">
<!ELEMENT RegisterArrayWindowInfo EMPTY>
<!ATTLIST RegisterArrayWindowInfo array IDREF #REQUIRED top CDATA "50" left CDATA "50" width CDATA "300" height CDATA "150" base (Decimal|Binary|Hexadecimal|Ascii|UnsignedDec|Unicode) "Decimal">
<!ELEMENT RAMWindowInfo EMPTY>
<!ATTLIST RAMWindowInfo ram IDREF #REQUIRED cellSize CDATA "1" top CDATA "50" left CDATA "50" width CDATA "450" height CDATA "450" contentsbase (Decimal|Binary|Hexadecimal|Ascii|UnsignedDec|Unicode) "Decimal" addressbase (Decimal|Binary|Hexadecimal) "Decimal">
]>

<Machine name="practical.cpu" >
	<!--............. Punctuation Options .............-->
	<PunctChar char="!" use="symbol" />
	<PunctChar char="#" use="symbol" />
	<PunctChar char="$" use="symbol" />
	<PunctChar char="%" use="symbol" />
	<PunctChar char="&amp;" use="symbol" />
	<PunctChar char="^" use="symbol" />
	<PunctChar char="_" use="symbol" />
	<PunctChar char="`" use="symbol" />
	<PunctChar char="*" use="symbol" />
	<PunctChar char="?" use="symbol" />
	<PunctChar char="@" use="symbol" />
	<PunctChar char="~" use="symbol" />
	<PunctChar char="+" use="symbol" />
	<PunctChar char="-" use="symbol" />
	<PunctChar char="(" use="token" />
	<PunctChar char=")" use="token" />
	<PunctChar char="," use="token" />
	<PunctChar char="/" use="token" />
	<PunctChar char="=" use="token" />
	<PunctChar char="[" use="token" />
	<PunctChar char="\" use="token" />
	<PunctChar char="]" use="token" />
	<PunctChar char="{" use="token" />
	<PunctChar char="|" use="token" />
	<PunctChar char="}" use="token" />
	<PunctChar char="." use="pseudo" />
	<PunctChar char=":" use="label" />
	<PunctChar char=";" use="comment" />

	<!--......... machine instruction fields ............-->
	<Field name="REGISTER" type="required" numBits="16" relativity="absolute" signed="false" defaultValue="0" id="model.Field30fc489f">
	</Field>
	<Field name="ADDR" type="required" numBits="12" relativity="absolute" signed="false" defaultValue="0" id="model.Field42a23c9d">
	</Field>
	<Field name="OP" type="required" numBits="4" relativity="absolute" signed="false" defaultValue="0" id="model.Field13f92235">
	</Field>

	<!--............. FileChannels .................-->
	<!-- none -->

	<!--............. registers .....................-->
	<Register name="AC" width="16" initialValue="0" readOnly="false" id="model.module.Register6fc8918a" />
	<Register name="AR" width="12" initialValue="0" readOnly="false" id="model.module.Register623e181a" />
	<Register name="DR" width="16" initialValue="0" readOnly="false" id="model.module.Register7b61c64d" />
	<Register name="E" width="1" initialValue="0" readOnly="false" id="model.module.Register7ea19a7b" />
	<Register name="I" width="1" initialValue="0" readOnly="false" id="model.module.Register448a8962" />
	<Register name="IR" width="16" initialValue="0" readOnly="false" id="model.module.Register186325ba" />
	<Register name="PC" width="12" initialValue="0" readOnly="false" id="model.module.Register409da32" />
	<Register name="S" width="1" initialValue="0" readOnly="false" id="model.module.Register1a4aa79b" />

	<!--............. register arrays ...............-->
	<!-- none -->

	<!--............. condition bits ................-->
	<ConditionBit name="CARRY-BIT" bit="0" register="model.module.Register7ea19a7b" halt="false" id="model.module.ConditionBit42f7e083" />
	<ConditionBit name="HALT-BIT" bit="0" register="model.module.Register1a4aa79b" halt="true" id="model.module.ConditionBit3fc0c7aa" />

	<!--............. rams ..........................-->
	<RAM name="MAIN" length="4096" cellSize="16" id="model.module.RAM2dd63bcc" />

	<!--............. set ...........................-->
	<!-- none -->

	<!--............. test ..........................-->
	<!-- none -->

	<!--............. increment .....................-->
	<Increment name="INCR-PC" register="model.module.Register409da32" delta="1" id="model.microinstruction.Increment1a5617b6" />

	<!--............. shift .........................-->
	<!-- none -->

	<!--............. logical .......................-->
	<!-- none -->

	<!--............. arithmetic ....................-->
	<!-- none -->

	<!--............. branch ........................-->
	<!-- none -->

	<!--............. transferRtoR ..................-->
	<TransferRtoR name="AR&lt;-IR(4-15)" source="model.module.Register186325ba" srcStartBit="4" dest="model.module.Register623e181a" destStartBit="0" numBits="12" id="model.microinstruction.TransferRtoR1b0f32be" />
	<TransferRtoR name="AR&lt;-PC" source="model.module.Register409da32" srcStartBit="0" dest="model.module.Register623e181a" destStartBit="0" numBits="12" id="model.microinstruction.TransferRtoR3802a70f" />

	<!--............. transferRtoA ..................-->
	<!-- none -->

	<!--............. transferAtoR ..................-->
	<!-- none -->

	<!--............. decode ........................-->
	<Decode name="DECODE-IR" ir="model.module.Register186325ba" id="model.microinstruction.Decode6cb90f22" />

	<!--............. set condition bit .............-->
	<!-- none -->

	<!--............. io ............................-->
	<!-- none -->

	<!--............. memory access .................-->
	<MemoryAccess name="IR&lt;-MAIN[AR]" direction="read" memory="model.module.RAM2dd63bcc" data="model.module.Register186325ba" address="model.module.Register623e181a" id="model.microinstruction.MemoryAccess7ca01ed" />

	<!--............. end ...........................-->
	<End id="model.microinstruction.End63ca3cc7" />

	<!--............. comment ...........................-->
	<!-- none -->

	<!--............. global equs ..................-->
	<!-- none -->

	<!--............. fetch sequence ................-->
	<FetchSequence>
		<Microinstruction microRef="model.microinstruction.TransferRtoR3802a70f" />
		<Microinstruction microRef="model.microinstruction.MemoryAccess7ca01ed" />
		<Microinstruction microRef="model.microinstruction.Increment1a5617b6" />
		<Microinstruction microRef="model.microinstruction.TransferRtoR1b0f32be" />
		<Microinstruction microRef="model.microinstruction.Decode6cb90f22" />
	</FetchSequence>

	<!--............. machine instructions ..........-->
	<!-- none -->

	<!--............. highlighting info .............-->
	<HighlightingInfo>
	</HighlightingInfo>

	<!--............. loading info ..................-->
	<LoadingInfo ram="model.module.RAM2dd63bcc" startingAddress="0" />

	<!--............. indexing info ............-->
	<IndexingInfo indexFromRight="false" />

	<!--............. program counter info ..................-->

</Machine>
