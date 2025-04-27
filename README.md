# Builder_Design_Pattern



Builder Design Pattern
----------------------

		* Solves the multiple constructor problem ( telescoping constructors )
		* static inner class (builder class)
		* internally required constructor
		* removes the need fo setters
		
Disadvandages :
--------------

		* Immutable
		* Inner static class
		* Designed first
		* Complex
		
Examples of Builder Pattern :
---------------------------


		1. String Builder
		2. Document Builder
		3. Locale.Builder
		4. Spring Reactive
		5. MockMvcBuilders
					 
		
1.

Phone.java :
----------

		public class Phone {

			public static class Builder {
				private String frontPanel;
				private String backPanel;
				private String processor;
				private String camera;

				public Builder() {
				}

				public Phone build() {
					return new Phone(this);
				}

				public Builder frontPanel(String frontPanel) {
					this.frontPanel = frontPanel;
					return this;
				}

				public Builder backPanel(String backPanel) {
					this.backPanel = backPanel;
					return this;
				}

				public Builder processor(String processor) {
					this.processor = processor;
					return this;
				}

				public Builder camera(String camera) {
					this.camera = camera;
					return this;
				}


			}

			private String frontPanel;
			private String backPanel;
			private String processor;
			private String camera;

			private Phone(Builder builder) {
				this.frontPanel = builder.frontPanel;
				this.backPanel = builder.backPanel;
				this.processor = builder.processor;
				this.camera = builder.camera;
			}

			public String getFrontPanel() {
				return frontPanel;
			}

			public String getBackPanel() {
				return backPanel;
			}

			public String getProcessor() {
				return processor;
			}

			public String getCamera() {
				return camera;
			}

			@Override
			public String toString() {
				final StringBuffer sb = new StringBuffer("Phone{");
				sb.append("frontPanel='").append(frontPanel).append('\'');
				sb.append(", backPanel='").append(backPanel).append('\'');
				sb.append(", processor='").append(processor).append('\'');
				sb.append(", camera='").append(camera).append('\'');
				sb.append('}');
				return sb.toString();
			}
		}
		
2. 

Builder.java :
-------------

			public class BuilderExample {

				public static void main(String[] args) {

					Phone.Builder builder = new Phone.Builder()
							.backPanel("Sandstone")
							.frontPanel("AMOLED")
							.camera("12 MP")
							.processor("Snapdragon 625");

					Phone phone = builder.build();

					System.out.println(phone);
					
				}

			}
