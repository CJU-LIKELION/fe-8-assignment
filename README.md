# 🦁 TypeScript 기초 (React 컴포넌트에 타입 적용하기)

**기존 JavaScript React 프로젝트에 TypeScript를 적용하여 타입 안정성 확보하기**

이번 미션에서는 이전 주차까지 구축한 아기사자 대시보드(React + JavaScript)에 TypeScript를 도입합니다. JavaScript 환경에서는 코드가 동작하더라도 예상치 못한 타입 관련 오류가 런타임에 발생할 위험이 있습니다. 모든 파일에 TypeScript를 적용(`jsx` -> `tsx`, `js` -> `ts`)하고, 데이터 구조, 컴포넌트의 `props`, `useState` 및 이벤트 핸들러 등에 명시적인 타입을 지정함으로써 컴파일 단계에서 오류를 방지하고 실무에서 요구되는 타입 안정성 확보 과정을 경험합니다.

**[참고 링크]**
자세한 내용은 PBL 사이트를 참고 하세요. [TypeScript 기초 - React 컴포넌트에 타입 적용하기](https://likelion-pbl-five.vercel.app/react/2f044860a4f481c0b69bce5e8eebfadb)

## 🎯 과제 목표

* JavaScript 프로젝트에서 발생할 수 있는 타입 관련 런타임 오류의 유형과 원인을 설명할 수 있다.
* **TypeScript의 기본 타입**(`string`, `number`, `boolean`, 배열, 객체 등)을 변수와 함수에 적용할 수 있다.
* `interface`와 `type`을 사용해 **복잡한 데이터 구조의 형태를 정의**할 수 있다.
* **React 컴포넌트의 props에 타입을 지정**하고, props 전달 시 타입 오류를 사전에 발견할 수 있다.
* `useState`의 제네릭을 활용해 **상태의 타입을 명시**할 수 있다.
* 이벤트 핸들러(`onChange`, `onClick`, `onSubmit` 등)의 **이벤트 객체 타입을 올바르게 지정**할 수 있다.
* 타입 정의를 별도 파일로 분리하여 여러 모듈에서 재사용하는 구조를 설명할 수 있다.

## 🛠 기술 스택

* **Language**: TypeScript (TSX), CSS
* **Framework**: React 19, React DOM
* **Routing**: React Router (`react-router-dom`)
* **Build Tool**: Vite (Yarn 패키지 매니저 사용)
* **Environment**: Web Browser (Chrome 권장)

## 📋 주요 기능

1. **타입 안정성이 확보된 대시보드**: 7주차에서 구현한 모든 기능(페이지 라우팅, 목록/상세 페이지, URL 쿼리 파라미터 연동, 명단 추가/삭제, 외부 데이터 불러오기 등)이 **동일하게 동작**해야 합니다.
2. **TypeScript 마이그레이션**: 기능 변경 없이 JavaScript 프로젝트를 TypeScript로 완전히 마이그레이션합니다.
3. **타입 검사 통과**: `tsc` 명령어로 타입 검사(`tsc -b`)를 실행했을 때 및 코드 편집기 상에서 어떠한 타입 오류도 표시되지 않아야 합니다.

## 🚀 실행 흐름 (Implementation Logic)

1. **프로젝트 환경 설정**: 기존 프로젝트 구조에서 확장자 변경(`tsx`, `ts`) 및 `tsconfig.json` 설정에 따라 개발 환경을 구성합니다. (`yarn install` -> `yarn dev`)
2. **데이터 타입 정의**: API 응답 데이터 및 애플리케이션 내 아기 사자 데이터의 구조를 `interface` 또는 `type`으로 정의합니다. (중첩 객체 포함)
3. **props 및 상태 타입 지정**: 모든 컴포넌트의 `props`와 `useState`의 상태(배열, 객체 폼 데이터, 원시 타입)에 정의한 타입을 적용합니다.
4. **이벤트 및 함수 타입 지정**: DOM 이벤트 핸들러의 이벤트 객체 속성과 유틸리티/API 호출 함수의 매개변수 및 반환값, Custom Hook의 반환값에 타입을 지정합니다.
5. **타입 분리**: 공통으로 사용되는 타입 정의는 `src/types/` 디렉토리에 별도 파일로 분리하여 재사용합니다.

## ⚠️ 제약 사항 및 유의 사항

* **TypeScript 설정**: `tsconfig.json`의 `strict` 옵션을 `true`로 유지해야 합니다. 불가피한 경우를 제외하고 `any` 타입 사용을 최소화하며, 구체적인 타입을 지정해야 합니다. 타입 단언(`as`)보다 타입 가드나 제네릭을 우선 사용합니다.
* **타입 정의 방식**: 컴포넌트 `props`는 `interface` 또는 `type`으로, React 제공 타입(`ChangeEvent`, `FormEvent`, `ReactNode` 등)을 적절히 활용해야 합니다.
* **라이브러리 허용 범위**: React 19, React DOM, react-router-dom, TypeScript만 사용 가능하며, `@types/react`, `@types/react-dom`은 `devDependencies`에 포함합니다. 상태 관리/UI/CSS 프레임워크는 금지됩니다.
* **React Hooks 사용 범위**: `useState`, `useEffect` 및 React Router 제공 훅만 사용 가능하며, 그 외 내장 훅(`useContext`, `useReducer` 등)은 사용할 수 없습니다.
* **스타일 유지**: 이전 주차 CSS 파일을 그대로 사용하며, CSS 파일을 TypeScript로 변환하지 않습니다. (import 에러 발생 시 `.d.ts` 파일 추가 가능)

---

*이 프로젝트는 [멋쟁이사자처럼(LIKELION) PBL](https://likelion-pbl-five.vercel.app/) 과정을 바탕으로 제작되었습니다.*
